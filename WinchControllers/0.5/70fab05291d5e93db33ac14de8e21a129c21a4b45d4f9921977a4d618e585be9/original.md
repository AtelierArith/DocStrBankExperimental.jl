```
mutable struct WCSettings
```

Settings of the WinchController

# Fields

  * `dt::Float64`: timestep of the winch controller
  * `test::Bool`: set to true for running the unit tests Default: false
  * `fac::Float64`: factor for I and P of lower force controller Default: 0.25
  * `max_iter::Int64`: max iterations limit for the PID solvers Default: 100
  * `iter::Int64`: actual max iterations of the PID solvers Default: 0
  * `t_startup::Float64`: startup time for soft start Default: 0.25
  * `t_blend::Float64`: blending time of the mixers in seconds Default: 0.25
  * `v_sat_error::Float64`: limitation of the reel-out speed error, used by the input saturation block of the speed controller Default: 1.0
  * `v_sat::Float64`: limitation of the reel-out speed , used by the output saturation block of the speed controller Default: 8.0
  * `v_ri_max::Float64`: maximal reel-in speed [m/s] Default: 8.0
  * `p_speed::Float64`: P value of the speed controller Default: 0.125
  * `i_speed::Float64`: I value of the speed controller Default: 4.0
  * `kb_speed::Float64`: back calculation constant for the anti-windup loop of the speed controller Default: 4.0
  * `kt_speed::Float64`: tracking constant of the speed controller Default: 5.0
  * `vf_max::Float64`: reel-out velocity where the set force should reach it's maximum Default: 2.75
  * `pf_low::Float64`: P constant of the lower force controller Default: 0.000144
  * `if_low::Float64`: I constant of the lower force controller Default: 0.0075 * 1.5
  * `df_low::Float64`: D constant of lower force controller Default: 2.0e-5 * 1.7
  * `nf_low::Float64`: filter constant n of upper force controller Default: 7.0
  * `kbf_low::Float64`: back calculation constant for the anti-windup loop of the lower force controller Default: 1.0
  * `ktf_low::Float64`: tracking constant of the lower force controller Default: 8.0
  * `f_low::Float64`: lower force limit [N] Default: 350
  * `f_reelin::Float64`: set force for reel-in phase [N] Default: 700
  * `f_high::Float64`: upper force limit [N] Default: 3800
  * `pf_high::Float64`: P constant of upper force controller Default: 0.000144 * 1.6
  * `if_high::Float64`: I constant of upper force controller Default: 0.0075 * 1.6
  * `df_high::Float64`: D constant of upper force controller Default: 2.0e-5 * 1.7
  * `nf_high::Float64`: filter constant n of upper force controller Default: 15.0
  * `kbf_high::Float64`: back calculation constant for the anti-windup loop of the upper force controller Default: 1.0
  * `ktf_high::Float64`: tracking constant of the upper force controller Default: 10.0
  * `winch_iter::Float64`: interations of the winch model Default: 10
  * `max_acc::Float64`: maximal acceleration of the winch (derivative of the set value of the reel-out speed) Default: 8.0
  * `kv::Float64`: proportional factor of the square root law, see function calc_vro Default: 0.06
