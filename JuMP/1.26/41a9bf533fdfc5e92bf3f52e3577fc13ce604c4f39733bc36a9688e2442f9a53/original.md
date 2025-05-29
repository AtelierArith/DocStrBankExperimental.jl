```
moi_function_type(::Type{T}) where {T}
```

Given a JuMP object type `T`, return the MathOptInterface equivalent.

See also: [`jump_function_type`](@ref).

## Example

```jldoctest
julia> moi_function_type(AffExpr)
MathOptInterface.ScalarAffineFunction{Float64}
```
