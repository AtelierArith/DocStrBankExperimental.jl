```
next_step!(s::AKM, integrator; set_speed = nothing, set_torque=nothing, set_force=nothing, bearing = nothing
           attractor=nothing, v_wind_gnd=s.set.v_wind, upwind_dir=-pi/2, dt=1/s.set.sample_freq)
```

次のシミュレーションステップを計算します。`set_speed`または`set_torque`のいずれかを提供する必要があります。

パラメータ:

  * s:            抽象的な凧モデルのインスタンス
  * integrator:   関数[`init_sim!`](@ref)によって返されるインテグレーターインスタンス
  * set_speed:         リールアウト速度の設定値（m/s）または何も指定しない
  * set_torque:   トルクの設定値（Nm）または何も指定しない
  * set_force:    力の設定値（N）または何も指定しない（ログ用のみ、他には使用されない）
  * bearing:      進行方向/コースの設定値（ラジアン）または何も指定しない（ログ用のみ、他には使用されない）
  * attractor:    引力座標[方位角、仰角]（ラジアン）または何も指定しない（ログ用のみ）
  * `v_wind_gnd`: 基準高さでの風速（m/s）
  * `upwind_dir`: 風上方向（ラジアン）、風が吹いてくる方向。ゼロは北、時計回りが正。デフォルト: -pi/2、西からの風。
  * dt:           時間ステップ（秒）

返り値: 時間ステップの終了時間（秒）。
