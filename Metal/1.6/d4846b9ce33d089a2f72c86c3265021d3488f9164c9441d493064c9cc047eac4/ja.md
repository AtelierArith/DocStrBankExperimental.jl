```
grid_origin_1d()::UInt32
grid_origin_2d()::NamedTuple{(:x, :y), Tuple{UInt32, UInt32}}
grid_origin_3d()::NamedTuple{(:x, :y, :z), Tuple{UInt32, UInt32, UInt32}}
```

スレッドがスレッドごとのステージインデータを読み取るためのグリッドの原点オフセットを返します。
