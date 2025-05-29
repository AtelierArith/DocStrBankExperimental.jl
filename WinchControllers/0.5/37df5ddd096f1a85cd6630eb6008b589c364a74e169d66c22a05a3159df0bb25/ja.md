```
mutable struct LowerForceController <: AbstractForceController
```

テザーの下部力のためのPIコントローラー。非アクティブな間は、トラッキング入力からの値を追跡します。バック計算は、アンチウィンドアップ手法およびトラッキングに使用されます。アンチウィンドアップの定数は `K_b`、トラッキングの定数は `K_t` です。次のブロックダイアグラムを実装します: ![lower_force_controller](assets/lower_force_controller.png)

## フィールド

  * `wcs::WinchControllers.WCSettings`
  * `integrator::WinchControllers.Integrator`: デフォルト: Integrator(wcs.dt)
  * `int2::WinchControllers.Integrator`: デフォルト: Integrator(wcs.dt)
  * `limiter::WinchControllers.RateLimiter`: デフォルト: RateLimiter(wcs.dt, wcs.max_acc)
  * `delay::WinchControllers.UnitDelay`: デフォルト: UnitDelay()
  * `reset::Bool`: デフォルト: false
  * `active::Bool`: デフォルト: false
  * `force::Float64`: デフォルト: 0
  * `f_set::Float64`: デフォルト: 0
  * `v_sw::Float64`: デフォルト: 0
  * `v_act::Float64`: デフォルト: 0
  * `tracking::Float64`: デフォルト: 0
  * `f_err::Float64`: デフォルト: 0
  * `last_err::Float64`: デフォルト: 0
  * `v_set_out::Float64`: デフォルト: 0
  * `sat_out::Float64`: デフォルト: 0
  * `res::StaticArraysCore.MVector{3, Float64}`: デフォルト: zeros(3)
