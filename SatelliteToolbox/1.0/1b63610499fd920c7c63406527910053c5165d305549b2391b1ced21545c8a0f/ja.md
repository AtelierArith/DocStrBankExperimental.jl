```
orbital_angular_velocity(a::Number, e::Number, i::Number; kwargs...) -> T
orbital_angular_velocity(orb::Orbit{Tepoch, T}; kwargs...) where {Tepoch<:Number, T<:Number} -> T
```

半長軸 `a` [m]、離心率 `e`、および傾斜 `i` [rad] を持つ軌道上の物体の角速度 [rad/s] を計算します。軌道は `orb` で指定することもできます（`Orbit` を参照）。

!!! note
    最初のシグネチャにおける出力型 `T` は、入力を浮動小数点型に昇格させることによって得られます。


# キーワード

  * `perturbation::Symbol`: 使用する摂動項を選択するためのシンボル。   (**デフォルト**: `:J2`)
  * `m0::Number`: 地球の標準重力パラメータ [m³ / s²]。   (**デフォルト** = `GM_EARTH`)
  * `J2::Number`: J₂ 摂動項。   (**デフォルト** = `EGM_2008_J2`)
  * `J4::Number`: J₄ 摂動項。   (**デフォルト** = `EGM_2008_J4`)
  * `R0::Number`: 地球の赤道半径 [m]。   (**デフォルト** = `EARTH_EQUATORIAL_RADIUS`)

# 摂動

キーワード引数 `perturbation` を使用して、計算に考慮される摂動項を選択できます。可能な値は次のとおりです。

  * `:J0`: ケプラー軌道を考慮します。
  * `:J2`: J2 までの摂動項を考慮します。
  * `:J4`: J2、J4、および J2² の摂動項を考慮します。

`perturbation` が省略された場合、デフォルトは `:J2` になります。
