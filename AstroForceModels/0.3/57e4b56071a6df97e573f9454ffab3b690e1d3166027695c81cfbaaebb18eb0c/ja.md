```
srp_accel(u::AbstractArray, sun_pos::AbstractArray, R_Sun::Number, R_Occulting::Number, Ψ::Number, RC::Number, t::Number; ShadowModel::ShadowModelType)
```

太陽放射圧からの加速度を計算する

太陽からの放射線が衛星の表面で反射し、衛星の軌道を乱す運動量を移動させます。この力は、次の方程式を用いてキャノンボールモデルを使用して計算できます。

```
            𝐚 = F * RC * Ψ * (AU/(R_sc_Sun))^2 * R̂_sc_Sun
```

!!! 注     現在、キャノンボールSRPのみがサポートされています。より高精度のドラッグを使用するには、状態変化関数を使用するか、さらに上流で弾道係数を計算してください。

# 引数

  * `u::AbstractArray`: 中心体の慣性系における宇宙船の現在の状態。
  * `sun_pos::AbstractArray`: 太陽の現在の位置。
  * `R_Sun::Number`: 太陽の半径。
  * `R_Occulting::Number`: 地球の半径。
  * `Ψ::Number`: 1天文単位での太陽定数。
  * `RC::Number`: 衛星の太陽弾道係数 – (面積/質量) * 反射率 [kg/m^2]。
  * `t::Number`: シミュレーションの現在の時間。

# オプション引数

  * `ShadowModel::ShadowModelType`: 使用するSRP地球影モデル。現在のオプション – :Conical, :Conical_Simplified, :Cylinderical

# 戻り値

  * `SVector{3}{Number}`: 第3の天体からの慣性加速度

```
