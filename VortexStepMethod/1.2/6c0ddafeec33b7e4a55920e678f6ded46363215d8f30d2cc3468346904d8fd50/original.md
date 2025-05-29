```
Solver
```

Main solver structure for the Vortex Step Method.See also: [solve](@ref)

# Attributes

## General settings

  * `aerodynamic_model_type`::Model = VSM: The model type, see: [Model](@ref)
  * density::Float64 = 1.225: Air density [kg/m³]
  * `max_iterations`::Int64 = 1500
  * `rtol`::Float64 = 1e-5: relative error
  * `tol_reference_error`::Float64 = 0.001
  * `relaxation_factor`::Float64 = 0.03: Relaxation factor for convergence

## Damping settings

  * `is_with_artificial_damping`::Bool = false: Whether to apply artificial damping
  * `artificial_damping`::NamedTuple{(:k2, :k4), Tuple{Float64, Float64}} = (k2=0.1, k4=0.0): Artificial damping parameters

## Additional settings

  * `type_initial_gamma_distribution`::InitialGammaDistribution = ELLIPTIC: see: [InitialGammaDistribution](@ref)
  * `core_radius_fraction`::Float64 = 1e-20:
  * mu::Float64 = 1.81e-5: Dynamic viscosity [N·s/m²]
  * `is_only_f_and_gamma_output`::Bool = false: Whether to only output f and gamma

## Solution

sol::VSMSolution = VSMSolution(): The result of calling [solve!](@ref) 
