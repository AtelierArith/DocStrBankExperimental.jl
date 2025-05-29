```
EnhancedConsoleLogger(stream::IO==stderr; kwargs...)
```

Replacement for the standard library `ConsoleLogger` that adds several usability improvements.

# Additional keyword arguments

The `EnhancedConsoleLogger` supports all of the standard keyword arguments accepted by `ConsoleLogger`. In addition, special behavior is defined for the following arguments:

  * `_pid`: prints in a column on the top right side of a log message. This keyword is  used internally by `WorkerLogger` to display the originating process for a  log message.
  * `_overwrite`: If `true`, then repetitions of the log message will be printed over to  avoid filling the screen with log messages.
  * `progress`: For a progress between 0 and 1, draw a progress bar on the right side  of the log message.
  * `_showlocation`: If true, print the location of the log message. Defaults to true for  `Debug`, `Warning`, and `Error` logs, and to false for `Info` logs.
