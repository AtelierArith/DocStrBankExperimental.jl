```
connectedelems(
    fes::AbstractFESet,
    node_list::Vector{IT},
    nmax::IT,
) where {IT<:Integer}
```

与えられたノードに接続されたfesのシリアル番号のリストを抽出します。
