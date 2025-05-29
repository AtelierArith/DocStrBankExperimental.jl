```
getindex(p, M::AbstractPowerManifold, i::Union{Integer,Colon,AbstractVector}...)
p[M::AbstractPowerManifold, i...]
```

点 `p` のインデックス `[i...]` にある要素を [`AbstractPowerManifold`](@ref) `M` に対して線形または多次元インデックスを使用してアクセスします。詳細は、Julia の [Array Indexing](https://docs.julialang.org/en/v1/manual/arrays/#man-array-indexing-1) を参照してください。
