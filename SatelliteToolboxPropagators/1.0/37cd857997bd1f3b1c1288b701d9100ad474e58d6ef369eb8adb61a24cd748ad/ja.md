```
j2osc_init!(j2oscd::J2OsculatingPropagator, orb₀::KeplerianElements) -> Nothing
```

平均ケプラー要素 `orb₀` を使用して J2 振動軌道伝播器構造 `j2oscd` を初期化します [SI 単位]。

!!! warning
    `j2oscd.j2d` の伝播定数 `j2c::J2PropagatorConstants` は変更されません。したがって、初期化する必要があります。

