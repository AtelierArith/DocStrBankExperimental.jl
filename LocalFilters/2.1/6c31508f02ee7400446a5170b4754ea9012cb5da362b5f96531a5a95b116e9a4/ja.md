```
LocalFilters.kernel_range([ord=FORWARD_FILTER,] rng::AbstractRange{<:Integer})
LocalFilters.kernel_range([ord=FORWARD_FILTER,] len::Integer)
LocalFilters.kernel_range([ord=FORWARD_FILTER,] start::Integer, stop::Integer)
```

は、範囲 `rng`、次元の長さ `len`、または最初と最後のインデックス `start` と `stop` に基づいて、単位ステップの `Int` 値のインデックス範囲を生成します。指定された次元の長さがある場合、その長さの中心範囲が返されます（偶数の長さの場合、`fftshift` と同じ規則が使用されます）。

指定された順序 `ord` がある場合、返される範囲はこの順序に適しています。

また、[`LocalFilters.kernel`](@ref)、[`LocalFilters.centered_offset`](@ref)、および [`LocalFilters.centered`](@ref) も参照してください。
