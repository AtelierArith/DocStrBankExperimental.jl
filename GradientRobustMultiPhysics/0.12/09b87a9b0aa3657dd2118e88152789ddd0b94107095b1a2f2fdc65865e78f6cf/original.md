```julia
struct FEVectorBlock{T, Tv, Ti, FEType, APT} <: AbstractArray{T, 1}
```

block of an FEVector that carries coefficients for an associated FESpace and can be assigned as an AbstractArray (getindex, setindex, size, length)
