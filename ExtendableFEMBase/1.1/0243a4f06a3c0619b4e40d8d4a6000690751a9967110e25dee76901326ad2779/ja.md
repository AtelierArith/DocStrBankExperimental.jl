```julia
struct AccumulatingVector{T} <: AbstractArray{T, 2}
```

AbstractArray{T, 2} として機能し、第二次元からのすべての値を自動的に累積するベクター

AV[k,j] += s は任意の j に対して AV.entries[k] += s になります。
