```
default_logger(args...)
```

Reset the `global_logger` to `Logging.ConsoleLogger`. Undoes the effect of [`smart_logger`](@ref). Arguments are passed on to `Logging.ConsoleLogger`.
