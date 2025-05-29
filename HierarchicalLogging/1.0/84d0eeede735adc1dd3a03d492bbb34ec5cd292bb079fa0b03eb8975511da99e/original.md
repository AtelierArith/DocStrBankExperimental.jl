```
set_logger!(loggers, key, logger)
```

Sets the logger associated with `key` in `loggers` to `logger`. 

If there is an existing value associated with `key` in `loggers`, it is overwritten. The new level of `key` is set to the maximum of the previous log level associated to `key` and the current level for `logger`.
