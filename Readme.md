# web.go

web.go is the simplest way to write web applications in the Go programming language. It's ideal for writing simple, performant backend web services. 

## Overview

Fork github.com/hoisie/web for use web.go in Google App Engine

## Installation

In App directory run:

```
$ git clone git://github.com/vodafon/appengine-web.git github.com/vodafon/appengine-web
```

Remove git files:

```
$ rm -rf github.com/vodafon/appengine-web/.git
$ rm -rf github.com/vodafon/appengine-web/.gitignore
$ rm -rf github.com/vodafon/appengine-web/Readme.md
```

### Write you app

```go
package hello

import (
    "github.com/vodafon/appengine-web"
    "net/http"
)

func init() {
    web.Get("/", root)

    http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
        web.Process(w, r)
    })
}

func root() string {
    return "Hello, Go"
}
```

### Add app.yaml

```
application: your-web-app
version: 1
runtime: go
api_version: go1

handlers:
- url: /static
  static_dir: static
- url: /.*
  script: _go_app
```

### Upload App

```
$ appcfg.py update .
```

## Documentation

API docs are hosted at http://webgo.io


## About

web.go was written by [Michael Hoisie](http://hoisie.com). 
