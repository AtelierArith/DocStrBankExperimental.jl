```
metida_table(args...; kwargs...)
```

MetidaTableを作成します。

AbstractIDResultの場合：

```
metida_table(obj::DataSet{RD}; order = nothing, results = nothing, ids = nothing)
```

ここで、obj <: DataSet{<:AbstractIDResult} order - 列の順序（列名のベクター）；results - 結果の列；ids - IDの列；
