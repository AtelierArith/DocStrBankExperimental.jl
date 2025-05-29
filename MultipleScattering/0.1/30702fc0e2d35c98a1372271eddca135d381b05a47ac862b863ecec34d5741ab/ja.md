```
run(sim::FrequencySimulation, x, ω; basis_order=5)
```

シミュレーション `sim` を位置 `x` と角周波数 `ω` で実行します。

位置は SVector または Vector{SVector} であり、周波数は浮動小数点数または浮動小数点数のベクトルであることができます。
