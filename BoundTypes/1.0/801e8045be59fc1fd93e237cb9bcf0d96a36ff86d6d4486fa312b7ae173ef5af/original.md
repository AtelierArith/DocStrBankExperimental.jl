```
NumberNonNegative{T<:Number} <: BoundNumber{T}
NumberNonNegative{T}(x::Number)
```

A number constraint that enforces `x ≥ 0` for value `x` of type `T`.

## Examples

```jldoctest
julia> NumberNonNegative{Float64}(10.0)
10.0

julia> NumberNonNegative{Float64}(-10.0)
ERROR: ConstraintError: constraints of type NumberNonNegative violated.
Wrong value: -10.0 must be a positive or zero (x ≥ 0).
[...]
```
