```
progress_map(f, c...; mapfun=map, progress=Progress(...), kwargs...)
```

Run a `map`-like function while displaying progress.

`mapfun` can be any function, but it is only tested with `map`, `reduce` and `pmap`. `ProgressMeter.ncalls(::typeof(mapfun), ::Function, args...)` must be defined to specify the number of calls to `f`.
