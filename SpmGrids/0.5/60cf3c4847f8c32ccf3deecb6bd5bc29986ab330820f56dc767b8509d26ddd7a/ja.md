```
get_data(grid::SpmGrid, name::AbstractString,
    x_index::GridRange=:, y_index::GridRange=:, channel_index::GridRange=:;
    bwd::Bool=false)::SubArray{Float64}
```

指定されたポイント `x_index`、`y_index` に対して、チャネルまたはパラメータ `name` のデータを返します。チャネルデータは `channel_index` でもインデックス指定できます。`bwd` が `true` の場合、存在する場合は bwd チャネルが返されます。`view` が `true`（デフォルト）であれば、view(@ref Base.view) が返され、それ以外の場合はコピーが返されます。
