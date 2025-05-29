```
searchdists!(neighbors, distances, pₒ, method; mask=nothing)
```

点 `pₒ` の `neighbors` と `distances` を制限付き検索 `method` を使用して更新し、見つかった隣接点の数を返します。オプションで、ドメインのすべてのインデックスに対して `mask` を指定できます。

詳細については、[`BoundedNeighborSearchMethod`](@ref) を参照してください。
