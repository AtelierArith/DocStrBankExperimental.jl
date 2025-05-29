```
compute_delay(observatory::ObservatoryMPC{T}, t_r_utc::DateTime; kwargs...) where {T <: AbstractFloat}
```

エコー受信時間の周りで時間遅延観測量のテイラー級数展開を計算します。これにより、次の式を使用して自動微分によるドップラーを計算できます。

$$
\nu = -f\frac{d\tau}{dt},
$$

ここで、$f$は送信機の周波数（MHz）、$\tau$は受信時間$t$での時間遅延です。計算された値には、地球の姿勢、LOD、および極運動による補正が含まれます。

**注意:** `TaylorInterpolant`エフェメリスでのみ動作します。 [`PlanetaryEphemeris.TaylorInterpolant`](@ref)を参照してください。

# 引数

  * `observatory::ObservatoryMPC{T}`: 観測所。
  * `t_r_utc::DateTime`: エコー受信のUTC時間。

# キーワード引数

  * `tord::Int = 5`: テイラー展開の次数。
  * `niter::Int = 10`: 光時間解の反復回数。
  * `xve::EarthEph = earthposvel`: 地球のエフェメリス。
  * `xvs::SunEph = sunposvel`: 太陽のエフェメリス。
  * `xva::AstEph`: 小惑星のエフェメリス。

すべてのエフェメリスは、[J2000からのet秒]を受け取り、[バリセントリック位置（km）と速度（km/sec）]を返す必要があります。

!!! reference
    See https://doi.org/10.1086/116062.

