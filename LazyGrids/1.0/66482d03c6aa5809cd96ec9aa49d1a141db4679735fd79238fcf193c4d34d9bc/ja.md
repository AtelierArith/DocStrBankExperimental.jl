```
(xg, yg, ...) = ndgrid(v1, v2, ...)
```

`AbstractVector` 入力のための `ndgrid` タプルを構築します。各出力は、対応する入力ベクトルタイプに応じた遅延グリッドタイプ（`AbstractGrid` のサブタイプ）を持ちます。

# 例

```jldoctest
julia> xg, yg = ndgrid(1:3, [:a, :b])
([1 1; 2 2; 3 3], [:a :b; :a :b; :a :b])

julia> xg
3×2 LazyGrids.GridUR{Int64, 1, 2}:
 1  1
 2  2
 3  3

julia> yg
3×2 LazyGrids.GridAV{Symbol, 2, 2}:
 :a  :b
 :a  :b
 :a  :b
```
