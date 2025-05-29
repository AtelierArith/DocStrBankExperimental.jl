```
mergedims(dims, old_dims => new_dim, others::Pair...) => dims_new
```

次元 `old_dims`、`new_dim` などが `dims` に見つかった場合、すべての `old_dims` の次元が単一の次元 `new_dim` に結合された新しい `dims_new` を返します。返される次元は `new_dim` の名前のみを保持します。その座標は `old_dims` の次元の座標の [`MergedLookup`](@ref) になります。新しい次元は常に `dims_new` の最後に配置されます。`others` にはマージされる他の次元ペアが含まれます。

# 例

```jldoctest
julia> using DimensionalData

julia> ds = (X(0:0.1:0.4), Y(10:10:100), Ti([0, 3, 4]))
(↓ X  0.0:0.1:0.4,
→ Y  10:10:100,
↗ Ti [0, 3, 4])

julia> mergedims(ds, (X, Y) => :space)
(↓ Ti    [0, 3, 4],
→ space MergedLookup{Tuple{Float64, Int64}} [(0.0, 10), (0.1, 10), …, (0.3, 100), (0.4, 100)] (↓ X, → Y))
```
