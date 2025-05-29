```
initial_condition_discontinuous_well_balancedness(x, t, equations::AbstractShallowWaterEquations, mesh)
```

この学術的な静止湖のテストケースのために、真に不連続な底面地形関数を設定します。すなわち、`eta`は一定で、`v`はどこでもゼロです。この静止湖のテストケースの誤差 `∫|η-η₀|` は、機械的な丸め誤差の周りであるべきです。
