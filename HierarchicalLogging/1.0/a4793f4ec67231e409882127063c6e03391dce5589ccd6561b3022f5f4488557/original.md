```
min_enabled_level!(h::HierarchicalLogger, key, level; [force=true], [recurse=true]) -> LogLevel
```

Recursively sets the level of logger `L` associated with `key` in `h`. 

If `haskey(h, key)`, sets the logging level of `L` (and, if `recurse == true`, the level of all of its children) to `level`. If the current logging level of `L` is greater than `level`, this method will not change the existing level if `force == false`.

If `haskey(h, key) == false`, a logger is added to `key` (with base logger `underlying_logger(closest_logger(h, key))`)

Returns the new `LogLevel` associated with `key`
