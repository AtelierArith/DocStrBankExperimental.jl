```
NumberInterval{T<:Number,A,L,R,B} <: BoundNumber{T}
NumberInterval{T,A,L,R,B}(x::Number)
```

A numeric constraint for a value `x` of type `T` which belongs to an interval between `A` and `B`. Parameters `L` and `R` are the comparison functions e.g `<` or `<=` which determine whether interval boundaries are included.

## Examples

```jldoctest
julia> NumberInterval{Float64,5,<,<=,10}(7.0)
7.0

julia> NumberInterval{Float64,5,<,<=,10}(10.0)
10.0

julia> NumberInterval{Float64,5,<,<=,10}(15.0)
ERROR: ConstraintError: constraints of type NumberInterval violated.
Wrong value: 15.0 must be in interval between 5 and 10.
[...]
```
