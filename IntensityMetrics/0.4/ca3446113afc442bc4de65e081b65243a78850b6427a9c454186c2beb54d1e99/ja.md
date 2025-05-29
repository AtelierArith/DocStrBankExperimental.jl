```
pn_pressure(pressures::Array{Unitful.Pressure, N})
```

ピーク負圧 [単位はそのまま]

`pressures` は最大4次元の配列であることが期待されます。最初の次元は時間で、残りの次元は空間です。
