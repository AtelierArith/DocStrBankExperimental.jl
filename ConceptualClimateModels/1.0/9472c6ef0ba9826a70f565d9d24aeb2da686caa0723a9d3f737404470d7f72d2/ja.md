```
plausible_grid(ds::DynamicalSystem, n = 101)
```

`ds`の[`plausible_limits`](@ref)をそれぞれカバーする`range`オブジェクトのタプルである`grid`を返します。`n`は整数または整数のベクトル（各次元用）にすることができます。得られた`grid`は`DynamicalSystems.AttractorsViaRecurrences`に渡すのに便利です。
