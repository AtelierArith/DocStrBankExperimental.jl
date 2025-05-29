```
random_pos([rng], sim, raster::Symbol, weights::Matrix)
```

確率行列 `weights` によって重み付けされたランダムな位置座標を持つ CartesianIndex を返します。

特定のセル/インデックスを選択する可能性は、その対応する値が `weights` 行列における値に比例します。

他にも [`random_pos(sim, raster)`](@ref) と [`random_cell`](@ref) を参照してください。
