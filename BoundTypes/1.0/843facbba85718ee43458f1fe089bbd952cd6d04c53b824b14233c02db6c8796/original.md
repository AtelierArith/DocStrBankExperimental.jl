```
NumberEven{T<:Number} <: BoundNumber{T}
NumberEven{T}(x::Number)
```

A numeric constraint to ensure that the value `x` of type `T` is even.

## Examples

```jldoctest
julia> NumberEven{Float64}(4.0)
4.0

julia> NumberEven{Float64}(5.0)
ERROR: ConstraintError: constraints of type NumberEven violated.
Wrong value: 5.0 must be even.
[...]
```
