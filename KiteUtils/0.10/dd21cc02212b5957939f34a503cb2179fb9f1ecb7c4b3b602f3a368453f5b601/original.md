```
SysState{P}
```

Basic system state. One of these is saved per time step. P is the number of tether particles.

  * `time::Float64`: time since start of simulation [s]
  * `t_sim::Float64`: time needed for one simulation timestep [s]
  * `sys_state::Int16`: state of system state control
  * `cycle::Int16`: cycle number
  * `fig_8::Int16`: number of the figure of eight of the current cycle
  * `e_mech::Float64`: mechanical energy [Wh]
  * `orient::StaticArraysCore.MVector{4, Float32}`: orientation of the kite (quaternion, order w,x,y,z)
  * `turn_rates::StaticArraysCore.MVector{3, Float32}`: turn rates around the body fixed x, y and z axis [rad/s]
  * `elevation::Float32`: elevation angle [rad]
  * `azimuth::Float32`: azimuth angle in wind reference frame [rad]
  * `l_tether::StaticArraysCore.MVector{4, Float32}`: tether length, tether 1 to 4 [m]
  * `v_reelout::StaticArraysCore.MVector{4, Float32}`: reelout speed, tether 1 to 4 [m/s]
  * `force::StaticArraysCore.MVector{4, Float32}`: tether force, tether 1 to 4 [N]
  * `depower::Float32`: depower settings [0..1]
  * `steering::Float32`: actual steering [-1..1]
  * `kcu_steering::Float32`: steering after the kcu, before applying offset and depower scaling [-1..1]
  * `set_steering::Float32`: set value of the steering [-1..1]
  * `heading::Float32`: heading angle [rad]
  * `heading_rate::Float32`: heading rate [rad/s]
  * `course::Float32`: course angle [rad]
  * `bearing::Float32`: bearing angle (set value of heading/ course) [rad]
  * `attractor::StaticArraysCore.MVector{2, Float32}`: attractor coordinates (azimuth, elevation) [rad]
  * `v_app::Float32`: norm of apparent wind speed [m/s]
  * `v_wind_gnd::StaticArraysCore.MVector{3, Float32}`: wind vector at reference height [m/s]
  * `v_wind_200m::StaticArraysCore.MVector{3, Float32}`: wind vector at 200m height [m/s]
  * `v_wind_kite::StaticArraysCore.MVector{3, Float32}`: wind vector at the height of the kite [m/s]
  * `AoA::Float32`: angle of attack [rad]
  * `side_slip::Float32`: side slip angle [rad]
  * `alpha3::Float32`: angle of attack at particle C [rad]
  * `alpha4::Float32`: angle of attack at particle D [rad]
  * `CL2::Float32`: lift coefficient
  * `CD2::Float32`: drag coefficient
  * `aero_force_b::StaticArraysCore.MVector{3, Float32}`: aerodynamic force in KB reference frame [N]
  * `aero_moment_b::StaticArraysCore.MVector{3, Float32}`: aerodynamic moment in KB reference frame [Nm]
  * `twist_angles::StaticArraysCore.MVector{4, Float32}`: twist angles for the 4 segment groups [rad]
  * `vel_kite::StaticArraysCore.MVector{3, Float32}`: velocity vector of the kite [m/s]
  * `acc::Float32`: acceleration [m/s²]
  * `X::StaticArraysCore.MVector{P, Float32} where P`: vector of particle positions in x [m]
  * `Y::StaticArraysCore.MVector{P, Float32} where P`: vector of particle positions in y [m]
  * `Z::StaticArraysCore.MVector{P, Float32} where P`: vector of particle positions in z [m]
  * `set_torque::StaticArraysCore.MVector{4, Float32}`: torque setting, winch 1..4       [Nm]
  * `set_speed::StaticArraysCore.MVector{4, Float32}`: speed setting, winch 1..4       [m/s]
  * `set_force::StaticArraysCore.MVector{4, Float32}`: force setting, winch 1..4         [N]
  * `roll::Float32`: roll angle [rad]
  * `pitch::Float32`: pitch angle [rad]
  * `yaw::Float32`: yaw angle [rad]
  * `var_01::Float32`: generic variable 01
  * `var_02::Float32`: generic variable 02
  * `var_03::Float32`: generic variable 03
  * `var_04::Float32`: generic variable 04
  * `var_05::Float32`: generic variable 05
  * `var_06::Float32`: generic variable 06
  * `var_07::Float32`: generic variable 07
  * `var_08::Float32`: generic variable 08
  * `var_09::Float32`: generic variable 09
  * `var_10::Float32`: generic variable 10
  * `var_11::Float32`: generic variable 11
  * `var_12::Float32`: generic variable 12
  * `var_13::Float32`: generic variable 13
  * `var_14::Float32`: generic variable 14
  * `var_15::Float32`: generic variable 15
  * `var_16::Float32`: generic variable 16
