```
heatratio(F::FluidState) = heatratio(temperature(F),fluid(F))
```

流体状態 `F` の温度における比熱比 `γ`（無次元）。
