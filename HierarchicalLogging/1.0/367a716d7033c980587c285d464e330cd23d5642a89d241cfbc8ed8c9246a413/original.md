```
insert_logger!(loggers::HierarchicalLogger, key, logger, [level=min_enabled_level(logger)])
```

Adds `logger` with associated `key` to `loggers`, if it does not exist.

Throws an `ArgumentException` if there is an existing logger in `loggers` with `key`
