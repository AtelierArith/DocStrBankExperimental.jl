```
project(data::DataMatrix, models, args...; verbose=true, kwargs...)
```

Convenience function for projection onto multiple `models`. Essentially calls `foldl` and prints some `@info` messages (if `verbose=true`). In most cases, it is better to call `project(data, base::DataMatrix)` instead of using this method directly.
