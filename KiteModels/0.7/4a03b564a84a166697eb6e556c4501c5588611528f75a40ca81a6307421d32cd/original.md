```
mutable struct KPS3{S, T, P} <: AbstractKiteModel
```

State of the kite power system. Parameters:

  * S: Scalar type, e.g. SimFloat In the documentation mentioned as Any, but when used in this module it is always SimFloat and not Any.
  * T: Vector type, e.g. MVector{3, SimFloat}
  * P: number of points of the system, segments+1

Normally a user of this package will not have to access any of the members of this type directly, use the input and output functions instead.

  * `set::KiteUtils.Settings`: Reference to the settings struct
  * `kcu::KitePodModels.KCU`: Reference to the KCU model (Kite Control Unit as implemented in the package KitePodModels
  * `am::AtmosphericModels.AtmosphericModel`: Reference to the atmospheric model as implemented in the package AtmosphericModels Default: AtmosphericModel()
  * `wm::Union{Nothing, WinchModels.AbstractWinchModel}`: Reference to winch model as implemented in the package WinchModels Default: nothing
  * `iter::Int64`: Iterations, number of calls to the function residual! Default: 0
  * `calc_cl::Dierckx.Spline1D`: Function for calculation the lift coefficent, using a spline based on the provided value pairs.
  * `calc_cd::Dierckx.Spline1D`: Function for calculation the drag coefficent, using a spline based on the provided value pairs.
  * `v_wind::Any`: wind vector at the height of the kite Default: zeros(S, 3)
  * `v_wind_gnd::Any`: wind vector at reference height Default: zeros(S, 3)
  * `v_wind_tether::Any`: wind vector used for the calculation of the tether drag Default: zeros(S, 3)
  * `v_apparent::Any`: apparent wind vector at the kite Default: zeros(S, 3)
  * `v_app_perp::Any`: vector, perpendicular to v*apparent; output of calc*drag Default: zeros(S, 3)
  * `alpha_2::Any`: angle of attack of the kite; output of set*cl*cd! Default: 0.0
  * `drag_force::Any`: drag force of kite and bridle; output of calc*aero*forces Default: zeros(S, 3)
  * `lift_force::Any`: lift force of the kite; output of calc*aero*forces Default: zeros(S, 3)
  * `steering_force::Any`: steering force acting on the kite; output of calc*aero*forces Default: zeros(S, 3)
  * `last_force::Any`: Default: zeros(S, 3)
  * `spring_force::Any`: spring force of the current tether segment, output of calc_res Default: zeros(S, 3)
  * `total_forces::Any`: Default: zeros(S, 3)
  * `force::Any`: sum of spring and drag forces acting on the current segment, output of calc_res Default: zeros(S, 3)
  * `unit_vector::Any`: unit vector in the direction of the current tether segment, output of calc_res Default: zeros(S, 3)
  * `av_vel::Any`: average velocity of the current tether segment, output of calc_res Default: zeros(S, 3)
  * `kite_y::Any`: y-vector of the kite fixed referense frame, output of calc*aero*forces Default: zeros(S, 3)
  * `segment::Any`: vector representing one tether segment (p1-p2) Default: zeros(S, 3)
  * `last_tether_drag::Any`: vector of the drag force of the last calculated tether segment Default: zeros(S, 3)
  * `vec_z::Any`: z vector of the kite reference frame Default: zeros(S, 3)
  * `res1::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: part one of the residual, difference between pos' and vel, non-flat, mainly for unit testing Default: zeros(SVector{P, KVec3})
  * `res2::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: part two of the residual, difference between vel' and acc, non-flat, mainly for unit testing Default: zeros(SVector{P, KVec3})
  * `pos::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: vector of the positions of the particles Default: zeros(SVector{P, KVec3})
  * `vel_kite::Any`: velocity vector of the kite Default: zeros(S, 3)
  * `seg_area::Any`: area of one tether segment [m²] Default: zero(S)
  * `bridle_area::Any`: total actual bridle area [m²] Default: zero(S)
  * `c_spring::Any`: spring constant, depending on the length of the tether segment Default: zero(S)
  * `segment_length::Any`: unstressed segment length [m] Default: 0.0
  * `damping::Any`: damping factor, depending on the length of the tether segment Default: zero(S)
  * `last_v_app_norm_tether::Any`: last norm of the apparent wind speed at a tether segment [m/s] Default: zero(S)
  * `param_cl::Any`: lift coefficient of the kite, depending on the angle of attack Default: 0.2
  * `param_cd::Any`: drag coefficient of the kite, depending on the angle of attack Default: 1.0
  * `cor_steering::Any`: correction term for the steering, in paper named i_(s,c), Eq. 30 Default: zero(S)
  * `psi::Any`: azimuth angle in radian; inital value is zero Default: zero(S)
  * `beta::Any`: elevation angle in radian; initial value about 70 degrees Default: deg2rad((se()).elevation)
  * `alpha_depower::Any`: depower angle [deg] Default: 0.0
  * `t_0::Any`: relative start time of the current time interval Default: 0.0
  * `v_reel_out::Any`: reel out speed of the winch [m/s] Default: 0.0
  * `last_v_reel_out::Any`: reel out speed during the last time step Default: 0.0
  * `l_tether::Any`: unstretched tether length Default: 0.0
  * `rho::Any`: air density at the height of the kite Default: 0.0
  * `depower::Any`: actual relative depower setting,  must be between    0 .. 1.0 Default: 0.0
  * `steering::Any`: actual relative steering setting, must be between -1.0 .. 1.0 Default: 0.0
  * `kcu_steering::Any`: steering after the kcu, before applying offset and depower sensitivity, -1.0 .. 1.0 Default: 0.0
  * `stiffness_factor::Any`: factor for the tether stiffness, used to find the steady state with a low stiffness first Default: 1.0
  * `initial_masses::StaticArraysCore.MVector{P, S} where {S, P}`: initial masses of the point masses Default: ones(P)
  * `masses::StaticArraysCore.MVector{P, S} where {S, P}`: current masses, depending on the total tether length Default: ones(P)
  * `forces::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: vector of the forces, acting on the particles Default: zeros(SVector{P, KVec3})
  * `sync_speed::Union{Nothing, S} where S`: synchronous speed of the motor/ generator Default: 0.0
  * `set_torque::Union{Nothing, S} where S`: set_torque of the motor/generator Default: nothing
