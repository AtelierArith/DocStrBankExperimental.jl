```
periodogram(y, t, normalisation = "default"; apply_end_matching = false, subtract_mean = true)
```

データ y の周期グラムを時間スタンプ t を使用して高速フーリエ変換 (FFT) により計算します。

周期グラムはデータのフーリエ変換の二乗の大きさとして計算されます。実際には、実数値の高速フーリエ変換 (rfft) を使用して周期グラムを計算します。

# 引数

  * `y::Array{Float64, 1}`: 時系列データ。
  * `t::Array{Float64, 1}`: 時間スタンプ。
  * `normalisation::Float64`: 正規化係数。デフォルトは 2Δt / length(t) です。
  * `apply_end_matching::Bool`: データにエンドマッチングを適用します。デフォルトは false です。
  * `subtract_mean::Bool`: データから平均を引きます。デフォルトは true です。
