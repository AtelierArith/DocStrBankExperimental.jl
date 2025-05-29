```
j4osc_init!(j4oscd::J4OsculatingPropagator, orb₀::KeplerianElements) -> Nothing
```

平均ケプラー要素 `orb₀` を使用して、J4振動軌道伝播器構造 `j4oscd` を初期化します。

!!! warning
    `j4oscd.j4d` の伝播定数 `j4c::J4PropagatorConstants` は変更されません。したがって、初期化する必要があります。

