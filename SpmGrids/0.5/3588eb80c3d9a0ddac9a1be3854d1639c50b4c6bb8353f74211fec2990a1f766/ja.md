```
get_parameter(grid::SpmGrid, name::AbstractString,
    x_index::GridRange=:, y_index::GridRange=:; view::Bool=true)::Union{Array{Float64},SubArray{Float64}}
```

指定された `x_index`、`y_index` の点でのパラメータ `name` の値を返します。`view` が `true`（デフォルト）であれば、view(@ref Base.view) が返され、それ以外の場合はコピーが返されます。
