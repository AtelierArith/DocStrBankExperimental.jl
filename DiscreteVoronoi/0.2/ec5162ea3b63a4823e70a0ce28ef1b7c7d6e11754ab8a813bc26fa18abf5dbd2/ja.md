```
jfa_voronoi!(grid::Matrix{T}, sites::Vector{T}; distance=euclidean) where {T<:SVector{2,Int}}
```

インプレースでボロノイ図を構築します。[ジャンプフラッディングアルゴリズム](https://en.wikipedia.org/wiki/Jump_flooding_algorithm)を使用します。このアルゴリズムは、グリッド内の空のセルが値 `SVector(0, 0)` を持ち、サイトがグリッド内にあると仮定します。
