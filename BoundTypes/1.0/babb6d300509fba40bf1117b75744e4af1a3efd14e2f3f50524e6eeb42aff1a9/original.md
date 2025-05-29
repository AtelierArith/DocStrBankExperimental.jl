```
NumberGreater{T<:Number,V} <: BoundNumber{T}
NumberGreater{T,V}(x::Number)
```

A number constraint that enforces `x > V` for value `x` of type `T`.

## Examples

```jldoctest
julia> NumberGreater{Float64,10.0}(20.0)
20.0

julia> NumberGreater{Float64,10.0}(5.0)
ERROR: ConstraintError: constraints of type NumberGreater violated.
Wrong value: 5.0 must be greater than 10.0.
[...]
```
