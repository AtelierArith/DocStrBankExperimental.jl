```
NumberNonPositive{T<:Number} <: BoundNumber{T}
NumberNonPositive{T}(x::Number)
```

A number constraint that enforces `x ≤ 0` for value `x` of type `T`.

## Examples

```jldoctest
julia> NumberNonPositive{Float64}(-10.0)
-10.0

julia> NumberNonPositive{Float64}(10.0)
ERROR: ConstraintError: constraints of type NumberNonPositive violated.
Wrong value: number 10.0 must be a negative or zero (x ≤ 0).
[...]
```
