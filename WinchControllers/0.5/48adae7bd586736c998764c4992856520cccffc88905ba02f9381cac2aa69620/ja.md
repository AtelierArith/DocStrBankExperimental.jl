```
mutable struct WinchController
```

基本的なウインチコントローラー。`wcsLowerForceLimit`、`wcsSpeedControl`、および `wcsUpperForceLimit` のいずれかのモードで動作します。

# フィールド

  * `wcs::WinchControllers.WCSettings`
  * `time::Float64`: デフォルト: 0
  * `v_set_pc::Union{Nothing, Float64}`: デフォルト: nothing
  * `v_set_in::Float64`: デフォルト: 0.0
  * `v_set_out::Float64`: デフォルト: 0.0
  * `v_set_ufc::Float64`: デフォルト: 0.0
  * `v_set_lfc::Float64`: デフォルト: 0.0
  * `v_set::Float64`: デフォルト: 0.0
  * `v_act::Float64`: デフォルト: 0.0
  * `force::Float64`: デフォルト: 0.0
  * `calc::WinchControllers.CalcVSetIn`: デフォルト: CalcVSetIn(wcs)
  * `mix3::WinchControllers.Mixer_3CH`: デフォルト: Mixer*3CH(wcs.dt, wcs.t*blend)
  * `sc::WinchControllers.SpeedController`: デフォルト: SpeedController(wcs)
  * `lfc::WinchControllers.LowerForceController`: デフォルト: LowerForceController(wcs)
  * `ufc::WinchControllers.UpperForceController`: デフォルト: UpperForceController(wcs)
