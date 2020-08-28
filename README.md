# Errors

A wrapper package over [pkg/errors](https://github.com/pkg/errors) to enrich and enhance error handling. This package was move out of [vcore/errors](https://github.com/Vernacular-ai/vcore/tree/master/errors) for indepenedent use and development for its first major release.

# Usage

To use this package, you need to have [pkg/errors](https://github.com/pkg/errors) and this package in your system. For most cases this should mean doing

```shell
go get github.com/pkg/errors
go get github.com/Vernacular-ai/errors
```

Then import this package as `import "github.com/Vernacular-ai/errors"`.

# Migration from vcore/errors

The major difference between this major release and the version in [vcore/errors](https://github.com/Vernacular-ai/vcore/tree/master/errors) is that functions have been demarcated with the functionality they provide and the context they are used in. So to simply create a new error, all you need to do is call the `NewError` functions with a message string. For example:

```go
err := NewError("Error happened")
```

Almost all of the functions support formatted string format so you can also do something like:
 
```go
num := 5
err := NewError("Errors occured %d times", num)
``` 
 
To chain a new error with an existing one, you need to use functions starting with the name *Chain*-. For example:

```go
err := NewError("Error happened")
err = ChainError(err, "This happened due to another error")
```

# Reference

All functions starting with *New*- in their name returns a fresh new error and those with *Chain*- in their name returns an `error` chained with the input `error`.

Check out the [docs](https://godoc.org/github.com/Vernacular-ai/errors) to know more.