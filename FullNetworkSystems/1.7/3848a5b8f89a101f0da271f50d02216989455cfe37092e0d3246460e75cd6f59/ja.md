```julia
struct GeneratorTimeSeries
```

発電機に関連する時間系列データで、デイアヘッドおよびリアルタイムの両方の定式化に必要です。`pu`で示される値は、基準電力100MWを前提としています。

フィールド:

  * `initial_generation::AxisKeys.KeyedArray{Float64, 1}`: 時間期間の開始時における発電機の発電量 (pu)
  * `offer_curve::AxisKeys.KeyedArray{Vector{Tuple{Float64, Float64}}, 2}`: 発電機のオファーカーブ。`KeyedArray`で、軸キーは`generator names x datetimes`
  * `regulation_min::AxisKeys.KeyedArray{Float64, 2}`: 補助サービス市場における発電機の最小出力 (pu)
  * `regulation_max::AxisKeys.KeyedArray{Float64, 2}`: 補助サービス市場における発電機の最大出力 (pu)
  * `pmin::AxisKeys.KeyedArray{Float64, 2}`: 発電機の最小出力 (pu)
  * `pmax::AxisKeys.KeyedArray{Float64, 2}`: 発電機の最大出力 (pu)
  * `regulation_offers::AxisKeys.KeyedArray{Union{Missing, Float64}, 2}`: 補助サービスの調整予備オファー価格 ($ /pu)。サービスを提供しない発電機は`missing`オファーデータを持ちます。
  * `spinning_offers::AxisKeys.KeyedArray{Union{Missing, Float64}, 2}`: 補助サービスのスピニング予備オファー価格 ($ /pu)。サービスを提供しない発電機は`missing`オファーデータを持ちます。
  * `on_supplemental_offers::AxisKeys.KeyedArray{Union{Missing, Float64}, 2}`: 補助サービスのオンライン補足予備オファー価格 ($ /pu)。サービスを提供しない発電機は`missing`オファーデータを持ちます。
  * `off_supplemental_offers::AxisKeys.KeyedArray{Union{Missing, Float64}, 2}`: 補助サービスのオフライン補足予備オファー価格 ($ /pu)。サービスを提供しない発電機は`missing`オファーデータを持ちます。
