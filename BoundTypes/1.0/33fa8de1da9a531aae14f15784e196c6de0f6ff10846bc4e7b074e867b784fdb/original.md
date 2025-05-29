```
NumberPositive{T<:Number} <: BoundNumber{T}
NumberPositive{T}(x::Number)
```

A number constraint that enforces `x > 0` for value `x` of type `T`.

## Examples

```jldoctest
julia> NumberPositive{Float64}(10.0)
10.0

julia> NumberPositive{Float64}(-10.0)
ERROR: ConstraintError: constraints of type NumberPositive violated.
Wrong value: number -10.0 must be a positive (x > 0).
[...]
```
