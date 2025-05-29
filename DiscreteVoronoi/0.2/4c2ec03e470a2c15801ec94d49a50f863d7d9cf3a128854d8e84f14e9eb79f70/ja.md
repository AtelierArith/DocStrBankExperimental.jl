```
naive_voronoi!(grid::Matrix{T}, sites::Vector{T}; distance=euclidean) where {T<:SVector{2,Int}}
```

最も基本的な方法でVoronoi図をインプレースで構築します：すべてのセルとすべての組み合わせをチェックします。
