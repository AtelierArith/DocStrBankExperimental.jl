```
eccentric_to_mean_anomaly(e::T1, E::T2) where {T1, T2} -> T
```

軌道の離心率 `e` と離心異常 `E` [rad] に基づいて平均異常 (0, 2π) [rad] を計算します。

!!! note
    出力型 `T` は `T1` と `T2` を浮動小数点に昇格させることによって得られます。

