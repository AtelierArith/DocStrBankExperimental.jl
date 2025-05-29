観測値のセットに対する対数確率値を計算します。

```julia
logprob(ndf, mass, obs, sigma, k)

```

## 必要な引数

  * `ndf::DataFrame`: パラメータセット b (b.1, b.2, ...) を持つ *ネストされた* データフレーム
  * `mass::Matrix{Floats64}`: サイズ(no of obs, length of b) の値
  * `obs`: 観測値
  * `sigma::Vector{Float64}`: logpdf 計算に使用されるシグマ値
  * `k::Int`: b ベクトルの長さ

## 戻り値

対数確率密度関数の値の Vector{Float64}
