```
grid_size_1d()::UInt32
grid_size_2d()::NamedTuple{(:x, :y), Tuple{UInt32, UInt32}}
grid_size_3d()::NamedTuple{(:x, :y, :z), Tuple{UInt32, UInt32, UInt32}}
```

スレッドがスレッドごとのステージインデータを読み取るためのグリッドの最大サイズを返します。
