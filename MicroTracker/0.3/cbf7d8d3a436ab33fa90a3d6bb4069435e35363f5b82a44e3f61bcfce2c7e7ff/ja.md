```
clip_trajectory_edges(linked_data::AbstractDataFrame, linking_settings::NamedTuple)
```

各軌道を反復処理し、粒子がフレーム外にある場合は追跡データを削除します。

粒子がフレーム外にあるのは、中心がビデオの端から粒子の半径内にあるときです。

[`find_trajectory_bounds`](@ref) を使用して、[`inbounds`](@ref) で軌道の境界を見つけます。
