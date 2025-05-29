```
get_active_volume(point_types::PointTypes{T}) where {T}
```

検出器のアクティブボリュームの近似値を、枯渇としてマークされたすべてのセルのセルボリュームを合計することによって返します。

## 引数

  * `point_types::PointTypes{T}`: [`Simulation`](@ref) のポイントタイプ。

## 例

```
get_active_volume(sim.point_types)
```

!!! note
    `φ`-対称性のみが考慮されます。

