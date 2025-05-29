```
orbital_angular_velocity_to_semimajor_axis(angvel::Number, e::Number, i::Number; kwargs...) -> T, Bool
```

角速度 `angvel` [rad / s] を持つ軌道の半長軸 [m] を計算します。この軌道は離心率 `e` と傾斜 `i` [rad] を持ちます。

角速度 `angvel` は、ノーダル周期、すなわち上昇ノードを通過する2回の連続した通過の間の時間に関連しています。

!!! note
    最初のシグネチャにおける出力型 `T` は、入力を浮動小数点型に昇格させることによって得られます。


# キーワード

  * `max_iterations::Int`: ニュートン-ラフソン法で許可される最大反復回数。   (**デフォルト** = 20)
  * `perturbation::Symbol`: 使用される摂動項を選択するためのシンボル。   (**デフォルト**: `:J2`)
  * `tolerance::Union{Nothing, Number}`: 数値法が収束したかどうかを確認するための残差許容値。もし `nothing` の場合、`√eps(T)` が使用されます。ここで `T` は計算のための内部型です。残差関数の単位は [deg / min] です。   (**デフォルト** = nothing)
  * `m0::Number`: 地球の標準重力パラメータ [m³ / s²]。   (**デフォルト** = `GM_EARTH`)
  * `J2::Number`: J₂ 摂動項。   (**デフォルト** = `EGM_2008_J2`)
  * `J4::Number`: J₄ 摂動項。   (**デフォルト** = `EGM_2008_J4`)
  * `R0::Number`: 地球の赤道半径 [m]。   (**デフォルト** = `EARTH_EQUATORIAL_RADIUS`)

# 戻り値

  * `T`: 半長軸 [m]。
  * `Bool`: 数値法が収束した場合は `true`、そうでない場合は `false`。

# 摂動

キーワード引数 `perturbation` は、計算に考慮される摂動項を選択するために使用できます。可能な値は次のとおりです。

  * `:J0`: ケプラー軌道を考慮します。
  * `:J2`: J2 までの摂動項を考慮します。
  * `:J4`: J2、J4、および J2² の摂動項を考慮します。

`perturbation` が省略された場合、デフォルトは `:J2` です。
