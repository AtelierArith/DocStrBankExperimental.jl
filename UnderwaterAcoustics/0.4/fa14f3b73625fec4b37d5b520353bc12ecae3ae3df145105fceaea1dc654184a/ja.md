```
absorption(frequency, distance=1000, salinity=35, temperature=27, depth=0, pH=8.1)
```

水中の体積音響吸収係数を計算します。与えられた条件は以下の通りです：

  * `frequency` は Hz
  * `distance` はメートル
  * `salinity` は ppt
  * 水の `temperature` は °C
  * `depth` はメートル
  * 水の `pH`

結果は、与えられた `distance` に対する音圧の単位のない線形スケール因子です。dB / m の吸収を得るには、`distance = 1.0` に設定し、結果をデシベルに変換します。例えば、周波数が 100 kHz の場合：

```julia-repl
julia> A = absorption(100e3, 1.0)
0.9959084838594522

julia> α = -20log10(A)
0.035611359656810865
```

フランソワとギャリソン（1982）モデルに基づく実装です。
