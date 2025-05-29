```
random_pos([rng], sim, raster::Symbol)
```

ランダムな位置座標を持つCartesianIndexを返します。

返されるインデックスは、各インデックスが同じ確率を持つラスタのインデックスからサンプリングされます。

また、[`random_pos(sim, raster, weights)`](@ref)および[`random_cell`](@ref)も参照してください。
