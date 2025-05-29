```
true_to_eccentric_anomaly(e::T1, f::T2) where {T1, T2} -> T
```

軌道の離心率 `e` と真の異常 `f` [rad] に基づいて、離心異常 (0, 2π) [rad] を計算します。

!!! note
    出力型 `T` は、`T1` と `T2` を浮動小数点に昇格させることによって得られます。

