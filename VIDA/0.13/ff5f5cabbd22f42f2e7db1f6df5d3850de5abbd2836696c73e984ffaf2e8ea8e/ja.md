```julia
struct VIDAMovie{T, F<:(ComradeBase.IntensityMap{T, 3, D, G, A} where {D, G<:(ComradeBase.AbstractRectiGrid{D}), A<:AbstractArray{T, 3}}), I} <: VIDA.AbstractMovie
```

# 詳細

X,Y,T `IntensityMap` と、連続的な映画を作成するための補間器を保持します。
