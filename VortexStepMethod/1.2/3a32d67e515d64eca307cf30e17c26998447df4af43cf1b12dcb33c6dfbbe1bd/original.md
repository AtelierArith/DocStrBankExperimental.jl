```
VSMSolution
```

Struct for storing the solution of the [solve!](@ref) function. Must contain all info needed by `KiteModels.jl`.

# Attributes

  * `panel_width_array`::Vector{Float64}: Width of the panels [m]
  * `alpha_array`::Vector{Float64}: Angle of attack of each panel relative to the apparent wind [rad]
  * cl_array::Vector{Float64}: Lift coefficients of the panels [-]
  * cd_array::Vector{Float64}: Drag coefficients of the panels [-]
  * cm_array::Vector{Float64}: Pitching moment coefficients of the panels [-]
  * panel_lift::Vector{Float64}: Lift force of the panels [N]
  * panel_drag::Vector{Float64}: Drag force of the panels [N]
  * panel_moment::Vector{Float64}: Pitching moment around the spanwise vector of the panels [Nm]
  * `f_body_3D`::Matrix{Float64}: Matrix of the aerodynamic forces (x, y, z vectors) [N]
  * `m_body_3D`::Matrix{Float64}: Matrix of the aerodynamic moments [Nm]
  * `gamma_distribution`::Union{Nothing, Vector{Float64}}: Vector containing the panel circulations.
  * force::MVec3: Aerodynamic force vector in KB reference frame [N]
  * moment::MVec3: Aerodynamic moments [Mx, My, Mz] around the reference point [Nm]
  * force_coeffs::MVec3: Aerodynamic force coefficients [CFx, CFy, CFz] [-]
  * `moment_coeffs`::MVec3: Aerodynamic moment coefficients [CMx, CMy, CMz] [-]
  * `moment_dist`::Vector{Float64}: Pitching moments around the spanwise vector of each panel. [Nm]
  * `moment_coeff_dist`::Vector{Float64}: Pitching moment coefficient around the spanwise vector of each panel. [-]
  * `solver_status`::SolverStatus: enum, see [SolverStatus](@ref)
