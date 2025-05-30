```
(p::CarbonChemistry)(; DIC, T, S, Alk = 0, pH = nothing,
                       return_pH = false,
                       boron = 0.000232 / 10.811 * S / 1.80655,
                       sulfate = 0.14 / 96.06 * S / 1.80655,
                       fluoride = 0.000067 / 18.9984 * S / 1.80655,
                       silicate = 0,
                       phosphate = 0,
                       upper_pH_bound = 14,
                       lower_pH_bound = 0)
```

`DIC`、`Alk`アルカリ度、`T`温度、`S`塩分を用いて海水中の`fCO₂`を計算します。ただし、`pH`が指定されている場合は中間計算の`pH`がスキップされ、`DIC`、`T`、`S`および`pH`から`pCO₂`が計算されます。

また、`return_pH`が`true`の場合は`pH`が返されます。
