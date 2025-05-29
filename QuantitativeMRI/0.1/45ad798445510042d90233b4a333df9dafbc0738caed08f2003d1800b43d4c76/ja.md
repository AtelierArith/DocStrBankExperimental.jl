```
T2Fit_Exp(ima::Array{T,N},t::AbstractVector{T},p0=nothing) where {T<:Real,N}
```

緩和パラメータ T2 を次の方程式でフィットします: $S(t) = M_0 \exp(-\frac{t}{T2})$。

# 引数

  * `ima::Array{T,N}`: 次元 [x,...,t] の画像。最後の次元 -> 時間次元
  * `t::AbstractVector{<:Real}`: ms 単位の時間ベクトル
  * `p0=nothing`: フィットのための初期値。空の場合は p0=[maximum(ima),30]

# キーワード

  * `removePoint::Bool=true`: フィット前に最初の点を削除するかどうか

# 戻り値

  * fit_params : パラメータマップ

      * M₀ マップ (単位なし)
      * T₂ マップ (ms)
