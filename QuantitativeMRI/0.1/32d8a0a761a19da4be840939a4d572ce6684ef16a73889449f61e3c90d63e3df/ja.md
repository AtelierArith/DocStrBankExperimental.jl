```
T2Fit_EpgNoise(ima::Array{T,4}, T1,TE,ETL,x0::Vector{Float64}) where T<:Real
```

定常$\Delta TE$および再焦点パルスを持つマルチスピンマルチエコーシーケンスの緩和パラメータT2をフィットします。EPGはMRIReco関数を用いて計算されます。ガウスノイズの標準偏差を計算するには、コイルの数`l`を知り、次の式を適用する必要があります：

$$
\sigma_g = \frac{\sigma}{\sqrt{2L}}
$$

# 引数

  * `ima::Array{T,N}`: エコーが最後の次元にある画像
  * `t::Union{Vector{<:Real},StepRange{<:Real,<:Real}}`: ms単位の時間ベクトル
  * `T1`: T1緩和時間
  * `TE`: エコー時間
  * `ETL`: エコートレイン長

# キーワード

# フィットされたマップを(x,y,z, M0,T2,delta (b1), Noise)の形式で返します

# 参考文献

## ノイズ

  * Cárdenas-Blanco A, Tejos C, Irarrazaval P, Cameron I. 大きさの磁気共鳴画像におけるノイズ。Concepts Magn Reson Part A [インターネット]. 2008年11月;32A(6):409–16. 利用可能: http://doi.wiley.com/10.1002/cmr.a.20124
  * Feng Y, He T, Gatehouse PD, Li X, Harith Alam M, Pennell DJ, et al. ノイズ補正による鉄負荷肝臓の改善されたMRI R 2 *緩和測定。Magn Reson Med [インターネット]. 2013年12月;70(6):1765–74. 利用可能: http://doi.wiley.com/10.1002/mrm.24607

## EPG

  * MRIReco.jlの実装

```
