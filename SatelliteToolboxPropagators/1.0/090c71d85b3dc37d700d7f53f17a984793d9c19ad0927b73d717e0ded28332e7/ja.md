```
j2_init!(j2d::J2Propagator, orb₀::KeplerianElements) -> Nothing
```

平均ケプラー要素 `orb₀` [SI単位] を使用して J2 軌道伝播器構造 `j2d` を初期化します。

!!! warning
    `j2d` 内の伝播定数 `j2c::J2PropagatorConstants` は変更されません。したがって、初期化する必要があります。

