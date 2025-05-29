```
mutable struct KPS4{S, T, P, Q, SP} <: AbstractKiteModel
```

State of the kite power system, using a 4 point kite model. Parameters:

  * S: Scalar type, e.g. SimFloat In the documentation mentioned as Any, but when used in this module it is always SimFloat and not Any.
  * T: Vector type, e.g. MVector{3, SimFloat}
  * P: number of points of the system, segments+1
  * Q: number of springs in the system, P-1
  * SP: struct type, describing a spring

Normally a user of this package will not have to access any of the members of this type directly, use the input and output functions instead.

  * `set::KiteUtils.Settings`: Reference to the settings struct
  * `kcu::KitePodModels.KCU`: Reference to the KCU model (Kite Control Unit as implemented in the package KitePodModels
  * `am::AtmosphericModels.AtmosphericModel`: Reference to the atmospheric model as implemented in the package AtmosphericModels Default: AtmosphericModel()
  * `wm::WinchModels.AbstractWinchModel`: Reference to winch model as implemented in the package WinchModels
  * `iter::Int64`: Iterations, number of calls to the function residual! Default: 0
  * `calc_cl::Dierckx.Spline1D`: Function for calculation the lift coefficient, using a spline based on the provided value pairs.
  * `calc_cd::Dierckx.Spline1D`: Function for calculation the drag coefficient, using a spline based on the provided value pairs.
  * `v_wind::Any`: wind vector at the height of the kite Default: zeros(S, 3)
  * `v_wind_gnd::Any`: wind vector at reference height Default: zeros(S, 3)
  * `v_wind_tether::Any`: wind vector used for the calculation of the tether drag Default: zeros(S, 3)
  * `v_apparent::Any`: apparent wind vector at the kite Default: zeros(S, 3)
  * `bridle_factor::Any`: bridle*factor = set.l*bridle/bridle_length(set) Default: 1.0
  * `side_cl::Any`: side lift coefficient, the difference of the left and right lift coefficients Default: 0.0
  * `drag_force::Any`: drag force of kite and bridle; output of calc*aero*forces! Default: zeros(S, 3)
  * `side_force::Any`: side_force acting on the kite Default: zeros(S, 3)
  * `f_d::Any`: Default: zeros(S, 3)
  * `f_s::Any`: Default: zeros(S, 3)
  * `ks::Any`: max_steering angle in radian Default: 0.0
  * `lift_force::Any`: lift force of the kite; output of calc*aero*forces! Default: zeros(S, 3)
  * `spring_force::Any`: spring force of the current tether segment, output of calc*particle*forces! Default: zeros(S, 3)
  * `last_force::Any`: last winch force Default: zeros(S, 3)
  * `res1::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: a copy of the residual one (pos,vel) for debugging and unit tests Default: zeros(SVector{P, KVec3})
  * `res2::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: a copy of the residual two (vel,acc) for debugging and unit tests Default: zeros(SVector{P, KVec3})
  * `pos::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: a copy of the actual positions as output for the user Default: zeros(SVector{P, KVec3})
  * `vel::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: a copy of the actual velocities as output for the user Default: zeros(SVector{P, KVec3})
  * `vel_kite::Any`: velocity vector of the kite Default: zeros(S, 3)
  * `segment_length::Any`: unstressed segment length [m] Default: 0.0
  * `param_cl::Any`: lift coefficient of the kite, depending on the angle of attack Default: 0.2
  * `param_cd::Any`: drag coefficient of the kite, depending on the angle of attack Default: 1.0
  * `psi::Any`: azimuth angle in radian; initial value is zero Default: zero(S)
  * `alpha_depower::Any`: depower angle [deg] Default: 0.0
  * `pitch::Any`: pitch angle [rad] Default: 0.0
  * `pitch_rate::Any`: pitch rate [rad/s] Default: 0.0
  * `alpha_2::Any`: aoa at particle B Default: 0.0
  * `alpha_3::Any`: aoa at particle C Default: 0.0
  * `alpha_4::Any`: aoa at particle D Default: 0.0
  * `side_slip::Any`: side_slip angle [rad] Default: 0.0
  * `t_0::Any`: relative start time of the current time interval Default: 0.0
  * `v_reel_out::Any`: reel out speed of the winch Default: 0.0
  * `last_v_reel_out::Any`: reel out speed at the last time step Default: 0.0
  * `l_tether::Any`: unstretched tether length Default: 0.0
  * `rho::Any`: air density at the height of the kite Default: 0.0
  * `depower::Any`: actual relative depower setting,  must be between    0 .. 1.0 Default: 0.0
  * `steering::Any`: actual relative steering setting, must be between -1.0 .. 1.0 Default: 0.0
  * `kcu_steering::Any`: steering after the kcu, before applying offset and depower sensitivity, -1.0 .. 1.0 Default: 0.0
  * `stiffness_factor::Any`: multiplier for the stiffniss of tether and bridle Default: 1.0
  * `initial_masses::StaticArraysCore.MVector{P, S} where {S, P}`: initial masses of the point masses Default: ones(P)
  * `masses::StaticArraysCore.MVector{P, S} where {S, P}`: current masses, depending on the total tether length Default: zeros(P)
  * `springs::StaticArraysCore.MVector`: vector of the springs, defined as struct Default: zeros(SP, Q)
  * `forces::StaticArraysCore.SVector{P, StaticArraysCore.MVector{3, Float64}} where P`: vector of the forces, acting on the particles Default: zeros(SVector{P, KVec3})
  * `sync_speed::Union{Nothing, S} where S`: synchronous speed of the motor/ generator Default: 0.0
  * `set_torque::Union{Nothing, S} where S`: set_torque of the motor/generator Default: nothing
  * `set_force::Union{Nothing, S} where S`: set value of the force at the winch, for logging only Default: nothing
  * `bearing::Union{Nothing, S} where S`: set value of the bearing angle in radians, for logging only Default: nothing
  * `attractor::Union{Nothing, StaticArraysCore.SVector{2, S}} where S`: coordinates of the attractor point [azimuth, elevation] in radian, for logging only Default: nothing
  * `x::Any`: x vector of kite reference frame Default: zeros(S, 3)
  * `y::Any`: y vector of kite reference frame Default: zeros(S, 3)
  * `z::Any`: z vector of kite reference frame Default: zeros(S, 3)
