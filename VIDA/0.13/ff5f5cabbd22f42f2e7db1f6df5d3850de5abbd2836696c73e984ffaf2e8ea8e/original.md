```julia
struct VIDAMovie{T, F<:(ComradeBase.IntensityMap{T, 3, D, G, A} where {D, G<:(ComradeBase.AbstractRectiGrid{D}), A<:AbstractArray{T, 3}}), I} <: VIDA.AbstractMovie
```

# Details

Holds a X,Y,T `IntensityMap` plus an interpolator that lets you make a continuous movie
