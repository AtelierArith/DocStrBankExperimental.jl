```
mutable struct SpeedController
```

ウインチの速度制御モードにおける巻き出し速度のPIコントローラ。非アクティブ時には、トラッキング入力からの値を追跡します。バックキャリブレーションは、アンチウィンドアップ手法およびトラッキングに使用されます。アンチウィンドアップの定数は `K_b`、トラッキングの定数は `K_t` です。次のブロックダイアグラムを実装します: ![speed_controller](assets/speed_controller.png)

## フィールド

  * `wcs::WinchControllers.WCSettings`
  * `integrator::WinchControllers.Integrator`: デフォルト: Integrator(wcs.dt)
  * `limiter::WinchControllers.RateLimiter`: デフォルト: RateLimiter(wcs.dt, wcs.max_acc)
  * `delay::WinchControllers.UnitDelay`: デフォルト: UnitDelay()
  * `v_act::Float64`: デフォルト: 0
  * `v_set_in::Float64`: デフォルト: 0
  * `inactive::Bool`: デフォルト: true
  * `tracking::Float64`: デフォルト: 0
  * `v_err::Float64`: デフォルト: 0
  * `v_set_out::Float64`: デフォルト: 0
  * `sat_out::Float64`: デフォルト: 0
  * `res::StaticArraysCore.MVector{2, Float64}`: デフォルト: zeros(2)
