```
random_cell([rng], sim, raster::Symbol, weights::Array)
```

シミュレーション `sim` からラスタ `raster` のランダムなセル ID を返します。特定のセルを選択する可能性は、そのセルに対応する `weights` 行列の値に比例します。

[`random_cell(sim, raster)`](@ref) および [`random_pos`](@ref) も参照してください。
