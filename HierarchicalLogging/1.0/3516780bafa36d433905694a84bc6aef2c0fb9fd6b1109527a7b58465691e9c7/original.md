```
min_enabled_level!(h::HierarchicalLogger, level; [force], [recurse]) -> LogLevel

Sets the logging level of the root logger in `h` to `level`. Any messages the root logger receives below `level` will be discarded and not logged.

Returns the minimum `LogLevel` over all loggers in `h`.
```
