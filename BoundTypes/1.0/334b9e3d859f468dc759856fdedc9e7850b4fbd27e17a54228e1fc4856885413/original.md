```
NumberNegative{T<:Number} <: BoundNumber{T}
NumberNegative{T}(x::Number)
```

A number constraint that enforces `x < 0` for value `x` of type `T`.

## Examples

```jldoctest
julia> NumberNegative{Float64}(-10.0)
-10.0

julia> NumberNegative{Float64}(10.0)
ERROR: ConstraintError: constraints of type NumberNegative violated.
Wrong value: 10.0 must be a negative (x < 0).
[...]
```
