魚の位置を追跡します

```
track(;pos_init::Matrix,
       tsave::AbstractVector = 1:100,
       bathymetry::GeoArrays.GeoArray,
       observations::Vector,
       observation_models::Vector{Function},
       sensor_positions::Vector,
       spatial_resolution,
       movement_std,
       save_filter::Bool = false,
       n_trajectories::Int = 0,
       show_progressbar::Bool = !is_logging(stderr),
       precision = Float32)
```

拡散モデルと平滑化に基づいて動物の位置を推定します。

# キーワード引数

  * `pos_init::Matrix`: 魚の位置の初期確率分布
  * `tsave::AbstractVector`: 確率マップが保存される時間ステップ。
  * `bathymetry`: `GeoArray`としての水深データ
  * `spatial_resolution`: `bathymetry`の空間解像度 [m]
  * `movement_std`: 1つの時間ステップ内での魚の動きの標準偏差 [m]
  * `observations`: すべての観測を保持するベクター。各要素は別々のセンサーの観測を含みます。
  * `observation_models::Vector{Function}`: 各センサーの観測モデルを含むベクター。
  * `sensor_positions`: 座標のタプルのベクターまたは `nothing`、すなわち `Vector{Union{Nothing, Tuple{Real, Real}}}`
  * `save_filter`: `true`の場合、フィルタ実行からの確率が返されます。
  * `n_trajectories=0`: サンプリングする軌跡の数
  * `show_progressbar = !is_logging(stderr)`: インタラクティブな使用のためにデフォルトで `true`。
  * `precision = Float32`: 計算に使用される数値浮動小数点型

注意、ベクター `observations`、`observation_models`、および `sensor_positions` の要素は同じ方法でソートされている必要があります。すなわち、ベクター内の同じ位置にある要素は同じセンサーを参照します。

# 戻り値

次の要素を持つ名前付きタプル：

  * `pos_smoother`: `tsave`のすべての時間ステップに対する魚の位置の平滑化された確率分布。
  * `residence_dist`: 居住分布。
  * `trajectories`: `n_trajectories` > 0 の場合はサンプリングされた軌跡、そうでなければ `nothing`。
  * `log_p`: 観測の対数確率。
  * `tsave`: 結果が保存される時間ステップのベクター。
  * `pos_filter`: 魚の位置のフィルタリングされた確率分布、`save_filter = true` の場合に含まれます。
