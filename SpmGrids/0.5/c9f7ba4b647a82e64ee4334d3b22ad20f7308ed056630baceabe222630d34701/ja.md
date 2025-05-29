```
get_channel(grid::SpmGrid, name::AbstractString,
    x_index::GridRange=:, y_index::GridRange=:, channel_index::GridRange=:;
    bwd::Bool=false)::SubArray{Float64}
```

指定された `x_index`、`y_index` のポイントでのチャネル `name` のデータを返します。チャネルデータは `channel_index` でインデックスできます。`bwd` が `true` の場合、存在する場合は bwd チャネルが返されます。`view` が `true`（デフォルト）であれば、view(@ref Base.view) が返され、それ以外の場合はコピーが返されます。
