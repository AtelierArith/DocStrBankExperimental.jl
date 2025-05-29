```
GenericAffExpr(constant::V, kv::AbstractArray{Pair{K,V}}) where {K,V}
```

Create a [`GenericAffExpr`](@ref) by passing a constant and a vector of pairs.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> GenericAffExpr(1.0, [x => 1.0])
x + 1
```
