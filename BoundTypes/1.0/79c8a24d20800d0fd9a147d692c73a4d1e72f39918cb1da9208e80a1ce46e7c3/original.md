```
NumberLess{T<:Number,V} <: BoundNumber{T}
NumberLess{T,V}(x::Number)
```

A number constraint that enforces `x < V` for value `x` of type `T`.

## Examples

```jldoctest
julia> NumberLess{Float64,10.0}(5.0)
5.0

julia> NumberLess{Float64,10.0}(20.0)
ERROR: ConstraintError: constraints of type NumberLess violated.
Wrong value: 20.0 must be less than 10.0.
[...]
```
