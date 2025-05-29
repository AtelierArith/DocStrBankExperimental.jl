```
getindex(p, M::ProductManifold, i::Union{Integer,Colon,AbstractVector})
p[M::ProductManifold, i]
```

点 `p` のインデックス `i` にある要素を [`ProductManifold`](@ref) `M` に対して線形インデックスを使用してアクセスします。Juliaの[配列インデックス](https://docs.julialang.org/en/v1/manual/arrays/#man-array-indexing-1)も参照してください。
