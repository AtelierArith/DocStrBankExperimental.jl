氷河のためのさまざまなバッファとデータセットを持つ2D気候を表す可変構造体。

```
Climate2D{F <: AbstractFloat}
```

# キーワード引数

  * `raw_climate::RasterStack`: シミュレーション全体の生気候データセット。
  * `climate_raw_step::RasterStack`: メモリ割り当てを避けるために現在のステップにトリミングされた生気候。
  * `climate_step::Dict`: 現在のステップの気候データ。
  * `climate_2D_step::Climate2Dstep`: 質量収支（MB）モデルに供給するための現在のステップの2D気候データ。
  * `longterm_temps::Vector{F}`: 氷のレオロジーのための長期温度。
  * `avg_temps::F`: 平均温度を計算するための中間バッファ。
  * `avg_gradients::F`: 平均勾配を計算するための中間バッファ。
