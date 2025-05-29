```
residuals(obs::Vector{RadarJPL{T}}; kwargs...)  where {T <: AbstractFloat}
```

レーダー天文学のO-C残差を計算し、地球の姿勢、LOD、および極運動による補正を含みます。

関連情報は[`compute_delay`](@ref)および[`radar_astrometry`](@ref)を参照してください。

# 引数

  * `obs::Vector{RadarJPL{T}}`: 観測のベクトル。

# キーワード引数

  * `tc::Real = 1.0`: エコー受信時間に対する時間オフセットで、範囲差によるドップラーシフトを計算します（秒）。オフセットは最も近いミリ秒に丸められます。
  * `autodiff::Bool = true`: [`compute_delay`](@ref)の自動微分を使用してドップラーシフトを計算するかどうか。
  * `tord::Int = 5`: テイラー展開の次数。
  * `niter::Int = 10`: 光時間解の反復回数。
  * `xve::EarthEph = earthposvel`: 地球のエフェメリス。
  * `xvs::SunEph = sunposvel`: 太陽のエフェメリス。
  * `xva::AstEph`: 小惑星のエフェメリス。

すべてのエフェメリスは[J2000からのet秒]を受け取り、[バリセンターの位置（km）と速度（km/sec）]を返す必要があります。
