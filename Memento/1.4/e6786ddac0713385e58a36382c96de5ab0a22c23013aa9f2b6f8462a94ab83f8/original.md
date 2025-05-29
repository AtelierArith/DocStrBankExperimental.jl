```
Logger
```

A `Logger` is responsible for converting msg strings into `Records` which are then passed to each handler. By default loggers propagate their message to their parent loggers.

# Fields

  * `name::AbstractString`: is the name of the logger (required).
  * `handlers::Dict{Any, Handler}`: is a collection of `Handler`s (defaults to empty `Dict`).
  * `level::AbstractString`: the current minimum logging level for the logger to  log message to handlers (defaults to "not_set").
  * `levels::Dict{AbstractString, Int}`: a mapping of available logging levels to their   relative priority (represented as integer values) (defaults to using `Memento._log_levels`)
  * `record::Type`: the `Record` type that should be produced by this logger   (defaults to `DefaultRecord`).
  * `propagate::Bool`: whether or not this logger should propagate its message to its parent   (defaults to `true`).
