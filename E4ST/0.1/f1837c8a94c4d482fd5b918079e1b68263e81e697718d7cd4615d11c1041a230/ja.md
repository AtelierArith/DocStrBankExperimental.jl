```
modify_setup_data!(mod::CCUS, config, data) -> nothing
```

次のことを行います：

  * `emis_co2` と `capt_co2_percent` に基づいて、捕集された炭素の列 `capt_co2` を追加します。
  * `capt_co2` によって `emis_co2` を減少させます。
  * 炭素捕集発電機を「塩水」と「EOR」の2つの別々の発電機に分割し、`config[eor_leakage_rate]` によってEORの排出量を調整します。
  * `ccus_type` の列を追加します - "eor"、"saline"、または "na" のいずれかです。
  * `data[:ccus_gen_sets]::Vector{Vector{Int64}}` にインデックスのセットを追加します。
