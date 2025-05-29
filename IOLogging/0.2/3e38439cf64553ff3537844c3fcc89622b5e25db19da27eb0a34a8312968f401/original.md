A generic logger for logging to any `IO`. Does not flush, as flushing is not a general IO operation. Also does not close the given IO.

```
IOLogger(logIOs = Dict(Info => stdout))
```

Logs logging events with LogLevel greater than or equal to `Info` to stdout, should no `logIOs` be given. In case two LogLevels are present, e.g. `Info` and `Error`, all logging events from `Info` up to (but excluding) `Error` will be logged to the stream given by `Info`. `Error` and above will be logged to the stream given by `Error`. It is possible to "clamp" logging events, by providing an upper bound that's logging to `devnull`. Beware, as the message will still be composed before writing to the actual stream (no hotwiring).

By default, exceptions occuring during logging are not caught. This is expected to change in the future, once it's decided how exceptions during logging should be handled.
