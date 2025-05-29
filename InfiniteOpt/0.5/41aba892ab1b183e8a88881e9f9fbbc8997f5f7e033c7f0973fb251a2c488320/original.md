```
JuMP.unset_time_limit_sec(model::InfiniteModel)
```

Extend `unset_time_limit_sec` to unset the time limit of the solver. Can be set  using `set_time_limit_sec`.

**Example**

```julia-repl
julia> unset_time_limit_sec(model)
```
