```
j4_init!(j4d::J4Propagator, orb₀::KeplerianElements) -> Nothing
```

平均ケプラー要素 `orb₀` を使用して J4 軌道伝播器構造 `j4d` を初期化します。

!!! warning
    `j4d` の伝播定数 `j4c::J4PropagatorConstants` は変更されません。したがって、初期化する必要があります。

