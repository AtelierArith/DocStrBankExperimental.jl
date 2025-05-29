```
dimension_indices_homvars(z::PVector{T, N})
dimension_indices_homvars(dims::NTuple{N, Int})
```

ベクトルごとに基になるデータをインデックス付けする `N` `(UnitRange, Int)` タプルのタプルを返します。各ベクトルの最後の座標は別々に扱われます。

## 例

```julia-repl
julia> v = PVector([4, 5, 6], [2, 3], [1, 2])
PVector{Int64, 3}:
 [4, 5, 6] × [2, 3] × [1, 2]

 julia> dimension_indices_homvars(v)
 ((1:2, 3), (4:4, 5), (6:6, 7))
```
