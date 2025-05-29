```
mutable struct LowerForceController <: AbstractForceController
```

PI controller for the lower force of the tether. While inactive, it tracks the value from the tracking input. Back-calculation is used as anti-windup method and for tracking. The constant for anti-windup is `K_b`, the constant for tracking `K_t` Implements the following block diagram: ![lower_force_controller](assets/lower_force_controller.png)

## Fields

  * `wcs::WinchControllers.WCSettings`
  * `integrator::WinchControllers.Integrator`: Default: Integrator(wcs.dt)
  * `int2::WinchControllers.Integrator`: Default: Integrator(wcs.dt)
  * `limiter::WinchControllers.RateLimiter`: Default: RateLimiter(wcs.dt, wcs.max_acc)
  * `delay::WinchControllers.UnitDelay`: Default: UnitDelay()
  * `reset::Bool`: Default: false
  * `active::Bool`: Default: false
  * `force::Float64`: Default: 0
  * `f_set::Float64`: Default: 0
  * `v_sw::Float64`: Default: 0
  * `v_act::Float64`: Default: 0
  * `tracking::Float64`: Default: 0
  * `f_err::Float64`: Default: 0
  * `last_err::Float64`: Default: 0
  * `v_set_out::Float64`: Default: 0
  * `sat_out::Float64`: Default: 0
  * `res::StaticArraysCore.MVector{3, Float64}`: Default: zeros(3)
