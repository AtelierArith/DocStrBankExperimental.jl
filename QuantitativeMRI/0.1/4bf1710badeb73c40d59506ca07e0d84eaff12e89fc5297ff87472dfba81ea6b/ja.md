```
T2Fit_ExpNoise(ima::Array{T,N},t::AbstractVector{<:Real},p0=nothing; kwargs...) where {T<:Real,N}
```

T2の緩和パラメータを次の方程式でフィットします: $S(t) = \sqrt{(M_0 \exp(-\frac{t}{T2}))^2 + 2 L \sigma_g^2}$ ここで、Lはチャンネルの数、$\sigma_g$は画像上のガウスノイズです。

# 引数

  * `ima::Array{T,N}`: 次元[x,...,t]の画像。最後の次元 -> 時間次元
  * `t::AbstractVector{<:Real}`: ms単位の時間ベクトル
  * `p0=nothing`: フィットのための開始値。空の場合はp0=[maximum(ima),30,maximum(ima)*0.1]

# キーワード

  * `removePoint::Bool=true`: フィッティングの前に最初の点を削除する
  * `L::Int=1`: コイル要素の数

# 戻り値

  * fit_params : パラメータマップ

      * M₀マップ（単位なし）
      * T₂マップ（ms）
      * ノイズマップ（単位なし）
  * fit_vec : 各ピクセルのフィットオブジェクト

# 参考文献

  * Cárdenas-Blanco A, Tejos C, Irarrazaval P, Cameron I. Noise in magnitude magnetic resonance images. Concepts Magn Reson Part A [Internet]. 2008 Nov;32A(6):409–16. Available from: http://doi.wiley.com/10.1002/cmr.a.20124
  * Feng Y, He T, Gatehouse PD, Li X, Harith Alam M, Pennell DJ, et al. Improved MRI R 2 * relaxometry of iron-loaded liver with noise correction. Magn Reson Med [Internet]. 2013 Dec;70(6):1765–74. Available from: http://doi.wiley.com/10.1002/mrm.24607

```
