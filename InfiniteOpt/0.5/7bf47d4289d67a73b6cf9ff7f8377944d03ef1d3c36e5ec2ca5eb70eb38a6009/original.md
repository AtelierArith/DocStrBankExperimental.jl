```
JuMP.set_optimizer_attribute(model::InfiniteModel, name::String, value)
```

Extend `set_optimizer_attribute` to specify a solver-specific attribute  identified by `name` to `value`.

**Example**

```julia-repl
julia> set_optimizer_attribute(model, "SolverSpecificAttributeName", true)
true
```
