```
mutable struct Logger{P, Q}
```

Struct to store a simulation log. P is number of points of the tether, segments+1 and  Q is the number of time steps that will be pre-allocated.

Constructor:

  * Logger(P, steps)

Fields:

  * `points::Int64`: Default: P
  * `index::Int64`: Default: 1
  * `time_vec::Vector{Float64}`: Default: zeros(Float64, Q)
  * `t_sim_vec::Vector{Float64}`: Default: zeros(Float64, Q)
  * `sys_state_vec::Vector{Int16}`: Default: zeros(Int16, Q)
  * `cycle_vec::Vector{Int16}`: Default: zeros(Int16, Q)
  * `fig_8_vec::Vector{Int16}`: Default: zeros(Int16, Q)
  * `e_mech_vec::Vector{Float64}`: Default: zeros(Float64, Q)
  * `orient_vec::Vector{StaticArraysCore.MVector{4, Float32}}`: Default: [zero(MVector{4, Float32}) for _ = 1:Q]
  * `turn_rates_vec::Vector{StaticArraysCore.MVector{3, Float32}}`: Default: [zero(MVector{3, MyFloat}) for _ = 1:Q]
  * `elevation_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `azimuth_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `l_tether_vec::Vector{StaticArraysCore.MVector{4, Float32}}`: Default: [zero(MVector{4, MyFloat}) for _ = 1:Q]
  * `v_reelout_vec::Vector{StaticArraysCore.MVector{4, Float32}}`: Default: [zero(MVector{4, MyFloat}) for _ = 1:Q]
  * `force_vec::Vector{StaticArraysCore.MVector{4, Float32}}`: Default: [zero(MVector{4, MyFloat}) for _ = 1:Q]
  * `depower_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `steering_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `kcu_steering_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `set_steering_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `heading_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `heading_rate_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `course_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `bearing_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `attractor_vec::Vector{StaticArraysCore.MVector{2, Float32}}`: Default: [zero(MVector{2, MyFloat}) for _ = 1:Q]
  * `v_app_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `v_wind_gnd_vec::Vector{StaticArraysCore.MVector{3, Float32}}`: Default: [zero(MVector{3, MyFloat}) for _ = 1:Q]
  * `v_wind_200m_vec::Vector{StaticArraysCore.MVector{3, Float32}}`: Default: [zero(MVector{3, MyFloat}) for _ = 1:Q]
  * `v_wind_kite_vec::Vector{StaticArraysCore.MVector{3, Float32}}`: Default: [zero(MVector{3, MyFloat}) for _ = 1:Q]
  * `AoA_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `side_slip_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `alpha3_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `alpha4_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `CL2_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `CD2_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `aero_force_b_vec::Vector{StaticArraysCore.MVector{3, Float32}}`: Default: [zero(MVector{3, MyFloat}) for _ = 1:Q]
  * `aero_moment_b_vec::Vector{StaticArraysCore.MVector{3, Float32}}`: Default: [zero(MVector{3, MyFloat}) for _ = 1:Q]
  * `twist_angles_vec::Vector{StaticArraysCore.MVector{4, Float32}}`: Default: [zero(MVector{4, MyFloat}) for _ = 1:Q]
  * `vel_kite_vec::Vector{StaticArraysCore.MVector{3, Float32}}`: Default: [zero(MVector{3, MyFloat}) for _ = 1:Q]
  * `acc_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `X_vec::Array{StaticArraysCore.MVector{P, Float32}, 1} where P`: Default: [zero(MVector{P, MyFloat}) for _ = 1:Q]
  * `Y_vec::Array{StaticArraysCore.MVector{P, Float32}, 1} where P`: Default: [zero(MVector{P, MyFloat}) for _ = 1:Q]
  * `Z_vec::Array{StaticArraysCore.MVector{P, Float32}, 1} where P`: Default: [zero(MVector{P, MyFloat}) for _ = 1:Q]
  * `set_torque_vec::Vector{StaticArraysCore.MVector{4, Float32}}`: Default: [zero(MVector{4, MyFloat}) for _ = 1:Q]
  * `set_speed_vec::Vector{StaticArraysCore.MVector{4, Float32}}`: Default: [zero(MVector{4, MyFloat}) for _ = 1:Q]
  * `set_force_vec::Vector{StaticArraysCore.MVector{4, Float32}}`: Default: [zero(MVector{4, MyFloat}) for _ = 1:Q]
  * `roll_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `pitch_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `yaw_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_01_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_02_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_03_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_04_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_05_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_06_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_07_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_08_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_09_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_10_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_11_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_12_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_13_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_14_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_15_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
  * `var_16_vec::Vector{Float32}`: Default: zeros(MyFloat, Q)
