```
JuMP.time_limit_sec(model::InfiniteModel)
```

Extend `time_limit_sec` to get the time limit (in seconds) of the solve used by  the optimizer model (`nothing` if unset). Can be set using `set_time_limit_sec`.

**Example**

```julia-repl
julia> time_limit_sec(model)
100
```
