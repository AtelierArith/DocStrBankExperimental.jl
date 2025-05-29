```
JuMP.set_time_limit_sec(model::InfiniteModel, limit)
```

Extend `set_time_limit_sec` to set the time limit (in seconds) of the solver. Can be unset using `unset_time_limit_sec` or with `limit` set to `nothing`.

**Example**

```julia-repl
julia> set_time_limit_sec(model, 100)
100
```
