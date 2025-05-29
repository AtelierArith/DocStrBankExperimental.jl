```
redac_voronoi!(grid::Matrix{T}, sites::Vector{T}; distance=euclidean, auxiliary=exact_aux) where {T<:SVector{2,Int}}
```

`dac_voronoi!`に似た分割統治法を実行しますが、追加のサイト排除ステップがあり、これにより後続のステップの作業を削減することを目的としています。
