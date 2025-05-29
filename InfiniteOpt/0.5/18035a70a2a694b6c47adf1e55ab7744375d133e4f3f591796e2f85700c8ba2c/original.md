```
JuMP.is_valid(model::InfiniteModel, vref::GeneralVariableRef)::Bool
```

Extend `JuMP.is_valid` to return `Bool` if `vref` is a valid reference.

**Example**

```julia-repl
julia> is_valid(model, vref)
true
```
