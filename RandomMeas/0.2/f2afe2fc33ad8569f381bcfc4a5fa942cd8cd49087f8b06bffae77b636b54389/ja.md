```
DenseShadow(measurement_probability::MeasurementProbability; G::Vector{Float64} = fill(1.0, length(u)))
```

事前に計算された確率テンソルから `DenseShadow` オブジェクトを構築します。

# 引数

  * `P::ITensor`: 測定結果を表す確率テンソル。
  * `u::Vector{ITensor}`: ローカルユニタリ変換のベクトル。
  * `G::Vector{Float64}` (オプション): 測定誤差を考慮するための G 値のベクトル（デフォルト: すべてのサイトに対して 1.0）。

# 戻り値

`DenseShadow` オブジェクト。
