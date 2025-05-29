```
dac_voronoi!(grid::Matrix{T}, sites::Vector{T}; distance=euclidean) where {T<:SVector{2,Int}}
```

[分割統治アルゴリズム](https://doi.org/10.1109%2Feit48999.2020.9208270)を使用して、インプレースでボロノイ図を構築します。
