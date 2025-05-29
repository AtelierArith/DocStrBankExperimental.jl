```
setbl!(data::DataSet{T}, bl, inds::Union{Vector{Int}, UnitRange{Int}, Tuple{Vararg{Int}}})
```

データ内の `ind` の範囲またはベクターに対してすべての被験者のベースラインを設定します。
