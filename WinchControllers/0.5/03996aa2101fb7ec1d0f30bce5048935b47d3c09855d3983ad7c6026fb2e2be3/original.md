```
mutable struct SpeedController
```

PI controller for the reel-out speed of the winch in speed control mode. While inactive, it tracks the value from the tracking input. Back-calculation is used as anti-windup method and for tracking. The constant for anti-windup is `K_b`, the constant for tracking `K_t` Implements the following block diagram: ![speed_controller](assets/speed_controller.png)

## Fields

  * `wcs::WinchControllers.WCSettings`
  * `integrator::WinchControllers.Integrator`: Default: Integrator(wcs.dt)
  * `limiter::WinchControllers.RateLimiter`: Default: RateLimiter(wcs.dt, wcs.max_acc)
  * `delay::WinchControllers.UnitDelay`: Default: UnitDelay()
  * `v_act::Float64`: Default: 0
  * `v_set_in::Float64`: Default: 0
  * `inactive::Bool`: Default: true
  * `tracking::Float64`: Default: 0
  * `v_err::Float64`: Default: 0
  * `v_set_out::Float64`: Default: 0
  * `sat_out::Float64`: Default: 0
  * `res::StaticArraysCore.MVector{2, Float64}`: Default: zeros(2)
