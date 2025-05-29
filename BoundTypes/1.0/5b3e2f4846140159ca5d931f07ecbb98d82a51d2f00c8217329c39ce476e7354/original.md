```
NumberOdd{T<:Number} <: BoundNumber{T}
NumberOdd{T}(x::Number)
```

A numeric constraint to ensure that the value `x` of type `T` is odd.

## Examples

```jldoctest
julia> NumberOdd{Float64}(5.0)
5.0

julia> NumberOdd{Float64}(4.0)
ERROR: ConstraintError: constraints of type NumberOdd violated.
Wrong value: 4.0 must be odd.
[...]
```
