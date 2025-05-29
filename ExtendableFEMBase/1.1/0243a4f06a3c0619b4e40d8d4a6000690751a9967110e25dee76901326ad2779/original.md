```julia
struct AccumulatingVector{T} <: AbstractArray{T, 2}
```

vector that is acting as an AbstractArray{T, 2} and  automatically accumulates all values from the second dimension

AV[k,j] += s for any j results in AV.entries[k] += s
