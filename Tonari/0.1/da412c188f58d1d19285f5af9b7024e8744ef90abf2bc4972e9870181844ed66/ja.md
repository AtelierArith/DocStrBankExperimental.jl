```
cross_periodogram(t, y₁, y₂, y₁_err = nothing, y₂_err = nothing; compute_coherence = true, apply_end_matching = false, subtract_mean = true)
```

2つの時系列y₁とy₂の間のクロス周期グラムを、時間スタンプtを使用して高速フーリエ変換（FFT）で計算します。

# 引数

  * `t::Array{Float64, 1}`: 時間スタンプ。
  * `y₁::Array{Float64, 1}`: 最初の時系列データ。あるいは複数の時系列の行列。
  * `y₂::Array{Float64, 1}`: 2番目の時系列データ。あるいは複数の時系列の行列。
  * `y₁_err::Array{Float64, 1}`: 最初の時系列の誤差。あるいは複数の時系列の誤差の行列。
  * `y₂_err::Array{Float64, 1}`: 2番目の時系列の誤差。あるいは複数の時系列の誤差の行列。
  * `compute_coherence::Bool`: 2つの時系列間のコヒーレンスを計算します。デフォルトはtrueです。
  * `apply_end_matching::Bool`: データにエンドマッチングを適用します。デフォルトはfalseです。
  * `subtract_mean::Bool`: データから平均を引きます。デフォルトはtrueです。

compute_coherenceがtrueの場合、関数は2つの時系列間のコヒーレンスを返します。そうでない場合、クロス周期グラムと2つの時系列の平均パワースペクトルを返します。オプションの戻り値については`coherence`関数を参照してください。

# 戻り値

  * `f::Array{Float64, 1}`: 周波数配列。
  * `C̄::Array{Complex{Float64}, 1}`: 平均クロス周期グラム。
  * `P̄₁::Array{Float64, 1}`: 最初の時系列の平均パワースペクトル。
  * `P̄₂::Array{Float64, 1}`: 2番目の時系列の平均パワースペクトル。
  * `C::Array{Complex{Float64}, 1}`: クロス周期グラム。
