```
NumberGreaterOrEqual{T<:Number,V} <: BoundNumber{T}
NumberGreaterOrEqual{T,V}(x::Number)
```

A number constraint that enforces `x ≥ V` for value `x` of type `T`.

## Examples

```jldoctest
julia> NumberGreaterOrEqual{Float64,10.0}(20.0)
20.0

julia> NumberGreaterOrEqual{Float64,10.0}(5.0)
ERROR: ConstraintError: constraints of type NumberGreaterOrEqual violated.
Wrong value: 5.0 must be greater or equal than 10.0.
[...]
```
