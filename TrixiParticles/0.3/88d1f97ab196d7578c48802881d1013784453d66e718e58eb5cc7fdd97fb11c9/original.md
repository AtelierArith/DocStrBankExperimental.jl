```
BoundarySPHSystem(initial_condition, boundary_model; movement=nothing, adhesion_coefficient=0.0)
```

System for boundaries modeled by boundary particles. The interaction between fluid and boundary particles is specified by the boundary model.

# Arguments

  * `initial_condition`: Initial condition (see [`InitialCondition`](@ref))
  * `boundary_model`: Boundary model (see [Boundary Models](@ref boundary_models))

# Keyword Arguments

  * `movement`: For moving boundaries, a [`BoundaryMovement`](@ref) can be passed.
  * `adhesion_coefficient`: Coefficient specifying the adhesion of a fluid to the surface.  Note: currently it is assumed that all fluids have the same adhesion coefficient.
