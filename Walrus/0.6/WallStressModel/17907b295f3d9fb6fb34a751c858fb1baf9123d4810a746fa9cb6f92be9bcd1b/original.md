```
WallStressBoundaryConditions(; von_Karman_constant = 0.4,
                               kinematic_viscosity = 1e-6,
                               B = 5.2,
                               precompute_speeds = [0:25/100000:25;],
                               grid = nothing)
```

Convenience constructor to setup `WallStress` boundary conditions.

# Keyword Arguments

  * `von_Karman_constant`: the von Karman wall stress constant
  * `kinematic_viscosity`: kinematic viscosity of the water above the wall
  * `B`: wall stress constant
  * `precomputed_friction_velocities`: precompute friction velocities?
  * `precompute_speeds`: bottom water speeds to precompute friction velocities for,  this should encompas the range of speeds possible in your simulation
  * `grid`: the grid to precompute the friction velocities for

# Example

```jldoctest
julia> using Walrus: WallStressBoundaryConditions

julia> using Oceananigans

julia> stress_boundary_conditions = WallStressBoundaryConditions()
(u = FluxBoundaryCondition: DiscreteBoundaryFunction (::WallStress{Float64, Nothing}) with parameters Val{:x}, v = FluxBoundaryCondition: DiscreteBoundaryFunction (::WallStress{Float64, Nothing}) with parameters Val{:y})
julia> boundary_conditions = (u = FieldBoundaryConditions(bottom = stress_boundary_conditions.u),
                              v = FieldBoundaryConditions(bottom = stress_boundary_conditions.v))
(u = Oceananigans.FieldBoundaryConditions, with boundary conditions
├── west: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── east: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── south: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── north: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── bottom: FluxBoundaryCondition: DiscreteBoundaryFunction (::WallStress{Float64, Nothing}) with parameters Val{:x}
├── top: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
└── immersed: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing), v = Oceananigans.FieldBoundaryConditions, with boundary conditions
├── west: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── east: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── south: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── north: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── bottom: FluxBoundaryCondition: DiscreteBoundaryFunction (::WallStress{Float64, Nothing}) with parameters Val{:y}
├── top: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
└── immersed: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing))
```
