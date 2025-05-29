```
dimension_indices(z::PVector{T, N})
dimension_indices(dims::NTuple{N, Int})

基になるデータをインデックス付けする `N` の `UnitRange` のタプルを返します。

## 例

```

julia-repl julia> v = PVector([4, 5, 6], [2, 3], [1, 2]) PVector{Int64, 3}:  [4, 5, 6] × [2, 3] × [1, 2]

julia> dimension_indices(v) (1:3, 4:5, 6:7) ```
