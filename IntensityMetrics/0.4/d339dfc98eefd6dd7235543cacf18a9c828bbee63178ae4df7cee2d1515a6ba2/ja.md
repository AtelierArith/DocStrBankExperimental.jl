```
intensity_sppa(pressures::Array{Unitful.Pressure, N}, medium::Medium, excitation::Excitation)
```

空間ピーク、パルス平均強度 [W/cm²]

`pressures` は最大4次元の配列であることが期待されます。最初の次元は時間で、残りの次元は空間です。
