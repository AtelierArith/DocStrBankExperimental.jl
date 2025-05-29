```
coefficient(v1::GenericVariableRef{T}, v2::GenericVariableRef{T}) where {T}
```

Return `one(T)` if `v1 == v2` and `zero(T)` otherwise.

This is a fallback for other [`coefficient`](@ref) methods to simplify code in which the expression may be a single variable.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> coefficient(x[1], x[1])
1.0

julia> coefficient(x[1], x[2])
0.0
```
