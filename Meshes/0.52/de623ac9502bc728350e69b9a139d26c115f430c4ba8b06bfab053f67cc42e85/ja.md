```
searchdists(pₒ, method, mask=nothing)
```

点 `pₒ` の隣接点と距離を、制限付き検索 `method` を使用して返します。オプションで、ドメインのすべてのインデックスに対して `mask` を指定できます。

詳細については、[`BoundedNeighborSearchMethod`](@ref) を参照してください。
