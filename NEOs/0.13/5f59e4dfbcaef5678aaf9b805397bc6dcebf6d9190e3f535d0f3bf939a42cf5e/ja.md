```
compute_radec(observatory::ObservatoryMPC{T}, t_r_utc::DateTime; kwargs...)
compute_radec(obs::RadecMPC{T}; kwargs...)
compute_radec(obs::Vector{RadecMPC{T}}; kwargs...) where {T <: Real}
```

MPC形式の観測データセットに対して天体の赤経と赤緯 [arcsec] を計算します。地球の姿勢、LOD、および極運動による補正が計算に考慮されます。

## 引数

  * `observatory::ObservatoryMPC{T}`: 観測地点。
  * `t_r_utc::DateTime`: 天体観測のUTC時間。
  * `obs::Vector{RadecMPC{T}}`: 光学観測。

## キーワード引数

  * `niter::Int`: 光到達時間解の反復回数 (デフォルト: `5`)。
  * `xve::EarthEph`: 地球のエフェメリス (デフォルト: `earthposvel`)。
  * `xvs::SunEph`: 太陽のエフェメリス (デフォルト: `sunposvel`)。
  * `xva::AstEph`: 小惑星のエフェメリス。

すべてのエフェメリスは [J2000からのet秒] を受け取り、[バリセントリック位置をkm、速度をkm/secで] 返す必要があります。
