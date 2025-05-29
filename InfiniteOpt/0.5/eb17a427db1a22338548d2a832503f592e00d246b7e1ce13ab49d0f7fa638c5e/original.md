```
JuMP.unset_silent(model::InfiniteModel)
```

Extend `JuMP.unset_silent` for infinite models to neutralize the effect of the `set_silent` function and let the solver attributes control the verbosity.

**Example**

```julia-repl
julia> unset_silent(model)
false
```
