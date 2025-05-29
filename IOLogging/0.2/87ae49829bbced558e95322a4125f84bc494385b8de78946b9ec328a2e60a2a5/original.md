A generic file logger for logging to files. Flushes the necessary output stream after each write (i.e. after each logging event) by default and closes the files on finalizing. Opened files are by default appended to. Given `append = false`, they will be overwritten.

```
FileLogger(logPaths = Dict(Info => "default.log"); flush = true, append = true)
```

Logs logging events with LogLevel greater than or equal to `Info` to "default.log", should no `logPaths` be given. In case two LogLevels are present, e.g. `Info` and `Error`, all logging events from `Info` up to (but excluding) `Error` will be logged to the file given by `Info`. `Error` and above will be logged to the file given by `Error`. It is possible to "clamp" logging events, by providing an upper bound that's logging to `/dev/null` on Unix/Mac or `NUL` on Windows. Beware, as the message will still be composed before writing to the actual file (no hotwiring).

By default, exceptions occuring during logging are not caught. This is expected to change in the future, once it's decided how exceptions during logging should be handled.
