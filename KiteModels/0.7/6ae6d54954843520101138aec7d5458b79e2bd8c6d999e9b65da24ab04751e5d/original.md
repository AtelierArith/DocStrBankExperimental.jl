```
mutable struct RamAirKite{S, V, P} <: AbstractKiteModel
```

State of the kite power system, using a quaternion kite model and three steering lines to the ground. Parameters:

  * S: Scalar type, e.g. SimFloat In the documentation mentioned as Any, but when used in this module it is always SimFloat and not Any.
  * V: Vector type, e.g. KVec3
  * P: number of tether points of the system, 3segments+3

Normally a user of this package will not have to access any of the members of this type directly, use the input and output functions instead.

  * `set::KiteUtils.Settings`: Reference to the settings struct
  * `wing::VortexStepMethod.RamAirWing`: Reference to the geometric wing model
  * `aero::VortexStepMethod.BodyAerodynamics`: Reference to the aerodynamic wing model
  * `vsm_solver::VortexStepMethod.Solver`: Reference to the VSM aerodynamics solver
  * `point_system::KiteModels.PointMassSystem`: Reference to the point mass system with points, segments, pulleys and tethers
  * `am::AtmosphericModels.AtmosphericModel`: Reference to the atmospheric model as implemented in the package AtmosphericModels Default: AtmosphericModel()
  * `pos::Matrix`: tether positions Default: zeros(S, 3, P)
  * `segment_lengths::Any`: unstressed segment lengths of the three tethers [m] Default: zeros(S, 3)
  * `t_0::Any`: relative start time of the current time interval Default: 0.0
  * `tether_lengths::Any`: unstretched tether length Default: zeros(S, 3)
  * `rho::Any`: air density at the height of the kite Default: 0.0
  * `masses::Any`: tether masses Default: zeros(S, P)
  * `c_spring::Any`: unit spring coefficient Default: zeros(S, 3)
  * `damping::Any`: unit damping coefficient Default: zeros(S, 3)
  * `torque_control::Bool`: whether or not to use torque control instead of speed control Default: false
  * `e_x::Any`: x vector of kite reference frame Default: zeros(S, 3)
  * `e_y::Any`: y vector of kite reference frame Default: zeros(S, 3)
  * `e_z::Any`: z vector of kite reference frame Default: zeros(S, 3)
  * `sys::Union{Nothing, ModelingToolkit.ODESystem}`: Simplified system of the mtk model Default: nothing
  * `vel_kite::Any`: Velocity of the kite Default: zeros(S, 3)
  * `I_b::Any`: Inertia around kite x y and z axis of the body frame Default: zeros(S, 3)
  * `u0map::Union{Nothing, Array{Pair{Symbolics.Num, S}, 1}} where S`: Initialization values for kite state Default: nothing
  * `p0map::Union{Nothing, Array{Pair{Symbolics.Num, S}, 1}} where S`: Initialization values for kite parameters Default: nothing
  * `bridle_fracs::Any`: X coordinate on normalized 2d foil of bridle attachments Default: [0.088, 0.31, 0.58, 0.93]
  * `crease_frac::Any`: Default: 0.82
  * `top_bridle_points::Vector`: The top bridle points that are not on the kite, in CAD frame Default: [[0.290199, 0.784697, -2.61305], [0.392683, 0.785271, -2.61201], [0.498202, 0.786175, -2.62148], [0.535543, 0.786175, -2.62148]]
  * `bridle_tether_diameter::Float64`: Tether diameter of tethers in bridle system [mm] Default: 2.0
  * `power_tether_diameter::Float64`: Tether diameter of the power tethers [mm] Default: 2.0
  * `steering_tether_diameter::Float64`: Tether diameter of the steering tethers [mm] Default: 1.0
  * `iter::Int64`: Number of solve! calls Default: 0
  * `unknowns_vec::Vector{Float64}`: Default: zeros(SimFloat, 3)
  * `set_set_values::Function`: Default: ()->begin         #= /home/terasaki/.julia/packages/KiteModels/fyU5V/src/ram*air*kite.jl:311 =#         nothing     end
  * `set_measure::Function`: Default: ()->begin         #= /home/terasaki/.julia/packages/KiteModels/fyU5V/src/ram*air*kite.jl:312 =#         nothing     end
  * `set_vsm::Function`: Default: ()->begin         #= /home/terasaki/.julia/packages/KiteModels/fyU5V/src/ram*air*kite.jl:313 =#         nothing     end
  * `set_unknowns::Function`: Default: ()->begin         #= /home/terasaki/.julia/packages/KiteModels/fyU5V/src/ram*air*kite.jl:314 =#         nothing     end
  * `get_state::Function`: Default: ()->begin         #= /home/terasaki/.julia/packages/KiteModels/fyU5V/src/ram*air*kite.jl:316 =#         nothing     end
  * `get_y::Function`: Default: ()->begin         #= /home/terasaki/.julia/packages/KiteModels/fyU5V/src/ram*air*kite.jl:317 =#         nothing     end
  * `prob::Union{Nothing, SciMLBase.ODEProblem}`: Default: nothing
  * `init_prob::Union{Nothing, SciMLBase.ODEProblem}`: Default: nothing
  * `integrator::Union{Nothing, OrdinaryDiffEqCore.ODEIntegrator, Sundials.CVODEIntegrator}`: Default: nothing
  * `init_integrator::Union{Nothing, OrdinaryDiffEqCore.ODEIntegrator, Sundials.CVODEIntegrator}`: Default: nothing
