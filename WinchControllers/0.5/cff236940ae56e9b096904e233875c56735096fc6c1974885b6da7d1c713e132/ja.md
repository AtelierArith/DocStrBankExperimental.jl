```
mutable struct UpperForceController <: AbstractForceController
```

テザーの上部力のためのPIDコントローラー。非アクティブな間、トラッキング入力からの値を追跡します。バック計算がアンチウィンドアップ手法およびトラッキングに使用されます。アンチウィンドアップの定数は `K_b`、トラッキングの定数は `K_t` です。次のブロックダイアグラムを実装します: ![upper_force_controller](assets/upper_force_controller.png)

# フィールド

  * `wcs::WinchControllers.WCSettings`
  * `integrator::WinchControllers.Integrator`: デフォルト: Integrator(wcs.dt)
  * `int2::WinchControllers.Integrator`: デフォルト: Integrator(wcs.dt)
  * `limiter::WinchControllers.RateLimiter`: デフォルト: RateLimiter(wcs.dt, wcs.max_acc)
  * `delay::WinchControllers.UnitDelay`: デフォルト: UnitDelay()
  * `reset::Bool`: デフォルト: false
  * `active::Bool`: デフォルト: false
  * `f_set::Float64`: デフォルト: 0
  * `v_sw::Float64`: デフォルト: 0
  * `v_act::Float64`: デフォルト: 0
  * `force::Float64`: デフォルト: 0
  * `tracking::Float64`: デフォルト: 0
  * `f_err::Float64`: デフォルト: 0
  * `v_set_out::Float64`: デフォルト: 0
  * `sat_out::Float64`: デフォルト: 0
  * `res::StaticArraysCore.MVector{3, Float64}`: デフォルト: zeros(3)

# 使用法

ウインチシステムの上部力制限を制御するインスタンスを作成します。
