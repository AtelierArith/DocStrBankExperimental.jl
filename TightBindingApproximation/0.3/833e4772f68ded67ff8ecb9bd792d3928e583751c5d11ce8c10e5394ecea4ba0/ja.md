```
FermiSurfaceData{S<:ReciprocalScatter} <: Data
```

フェルミ面のデータ、含まれるもの：

1. `values::S`: フェルミ面の点。
2. `weights::Matrix{Float64}`: フェルミ面に投影された特定の軌道のセットの重み。
