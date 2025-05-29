```
GenericAffExpr(constant::V, kv::Vararg{Pair{K,V},N}) where {K,V,N}
```

Create a [`GenericAffExpr`](@ref) by passing a constant and pairs of additional arguments.

## Examples

```jldoctest; setup=:(using JuMP; model = Model(); @variable(model, x)) julia> GenericAffExpr(1.0, x => 1.0) x + 1
