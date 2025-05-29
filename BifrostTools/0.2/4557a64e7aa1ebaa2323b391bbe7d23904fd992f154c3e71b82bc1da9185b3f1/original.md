```
function zup(
    arr::Array{T,3},
    periodic::Bool=true,
    order::Int=6
) where {T<:AbstractFloat}
```

Stagger operation on `arr` by a 5th order polynomial interpolation,  shifting the variable half a grid point upwards in the z-direction
