```
evaluate_at_grid_nodes(dh::AbstractDofHandler, u::AbstractVector{T}, fieldname::Symbol) where T
```

Dofハンドラ`dh`と解ベクトル`u`を用いて、グリッドのノード座標におけるフィールド`fieldname`の近似解を評価します。

長さ`getnnodes(grid)`のベクトルを返し、エントリ`i`にはノード`i`の座標における近似の評価が含まれます。フィールドがグリッドの一部に存在しない場合、そのノードに対する対応する値は`NaN`として返されます。
