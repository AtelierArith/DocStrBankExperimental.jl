```
radar_astrometry(observatory::ObservatoryMPC{T}, t_r_utc::DateTime, F_tx::Real; kwargs...) where {T <: AbstractFloat}
radar_astrometry(radar::RadarJPL{T}; kwargs...) where {T <: AbstractFloat}
radar_astrometry(astradarfile::String; kwargs...)
radar_astrometry(astradardata::Vector{RadarJPL}; kwargs...) where {T <: AbstractFloat}
```

時間遅延とドップラーシフトを返します。

# 引数

  * `observatory::ObservatoryMPC{T}`: 観測ステーション。
  * `t_r_utc::DateTime`: エコー受信のUTC時間。
  * `F_tx::Real`: 送信機の周波数（MHz）。
  * `radar::RadarJPL{T}` / `astradardata::Vector{RadarJPL{T}}`: レーダー観測。
  * `astradarfile::String`: レーダー観測を取得するファイル。

# キーワード引数

  * `tc::Real = 1.0`: エコー受信時間に対する時間オフセット、範囲の差によるドップラーシフトを計算するため（秒）。オフセットは最も近いミリ秒に丸められます。
  * `autodiff::Bool = true`: [`compute_delay`](@ref) の自動微分を使用してドップラーシフトを計算するかどうか。
  * `tord::Int = 5`: テイラー展開の次数。
  * `niter::Int = 10`: 光時間解の反復回数。
  * `xve::EarthEph = earthposvel`: 地球のエフェメリス。
  * `xvs::SunEph = sunposvel`: 太陽のエフェメリス。
  * `xva::AstEph`: 小惑星のエフェメリス。

すべてのエフェメリスは [J2000 からの et 秒] を受け取り、[バリセントリック位置（km）と速度（km/sec）] を返さなければなりません。
