```
get_timestep_load_served(
    solution::Dict{String,<:Any},
    network::Dict{String,<:Any}
)::Dict{String,Vector{Real}}
```

最適なディスパッチ `solution` からの負荷統計を返し、`network` の基準負荷（非シェッド）と比較し、以下の統計を提供します。

  * `"Feeder load (%)"`: フィーダーがサポートしている負荷の割合、
  * `"Microgrid load (%)"`: マイクログリッドがサポートしている負荷の割合、
  * `"Bonus load via microgrid (%)"`: どれだけの追加負荷がサポートされているか。

## 注意

現在、マイクログリッドはまだ明示的に定義されていないため（マイクログリッドタグ付けの初期実装については 'settings' ファイルを参照）、`"Bonus load via microgrid (%)"` はストレージでどれだけの充電が行われているかを示すだけです。
