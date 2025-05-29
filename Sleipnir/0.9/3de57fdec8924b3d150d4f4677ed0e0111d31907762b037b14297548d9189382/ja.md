```
get_cumulative_climate!(climate, period; gradient_bounds=[-0.009, -0.003], default_grad=-0.0065)
```

与えられた期間の累積気候データを計算して更新します。

# キーワード引数

  * `climate::Climate`: 生の気候データを含む気候オブジェクト。
  * `period::Period`: 累積気候データを計算する期間。
  * `gradient_bounds::Vector{Float64}`: オプション。勾配値を制限する範囲。デフォルトは `[-0.009, -0.003]`。
  * `default_grad::Float64`: オプション。使用するデフォルトの勾配値。デフォルトは `-0.0065`。

# 更新内容

  * `climate.climate_raw_step`: 与えられた期間の生の気候データ。
  * `climate.avg_temps`: 与えられた期間の平均気温。
  * `climate.avg_gradients`: 与えられた期間の平均勾配。
  * `climate.climate_step["prcp"]`: 与えられた期間の累積降水量。
  * `climate.climate_step["temp"]`: 与えられた期間の累積気温。
  * `climate.climate_step["gradient"]`: 与えられた期間の累積勾配。
  * `climate.climate_step["avg_temp"]`: 与えられた期間の平均気温。
  * `climate.climate_step["avg_gradient"]`: 与えられた期間の平均勾配。
  * `climate.climate_step["ref_hgt"]`: 生の気候データのメタデータからの参照高さ。
