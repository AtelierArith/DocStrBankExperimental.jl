```
mutable struct WinchController
```

Basic winch controller. Works in one of the three modes `wcsLowerForceLimit`, `wcsSpeedControl` and `wcsUpperForceLimit`.

# Fields

  * `wcs::WinchControllers.WCSettings`
  * `time::Float64`: Default: 0
  * `v_set_pc::Union{Nothing, Float64}`: Default: nothing
  * `v_set_in::Float64`: Default: 0.0
  * `v_set_out::Float64`: Default: 0.0
  * `v_set_ufc::Float64`: Default: 0.0
  * `v_set_lfc::Float64`: Default: 0.0
  * `v_set::Float64`: Default: 0.0
  * `v_act::Float64`: Default: 0.0
  * `force::Float64`: Default: 0.0
  * `calc::WinchControllers.CalcVSetIn`: Default: CalcVSetIn(wcs)
  * `mix3::WinchControllers.Mixer_3CH`: Default: Mixer*3CH(wcs.dt, wcs.t*blend)
  * `sc::WinchControllers.SpeedController`: Default: SpeedController(wcs)
  * `lfc::WinchControllers.LowerForceController`: Default: LowerForceController(wcs)
  * `ufc::WinchControllers.UpperForceController`: Default: UpperForceController(wcs)
