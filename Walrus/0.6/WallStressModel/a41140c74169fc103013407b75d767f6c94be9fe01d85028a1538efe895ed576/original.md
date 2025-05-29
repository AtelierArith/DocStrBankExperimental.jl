```
WallStress(; von_Karman_constant = 0.4,
             kinematic_viscosity = 1e-6,
             B = 5.2,
             precomputed_friction_velocities = false,
             precompute_speeds = [0:25/100000:25;],
             grid = nothing,
             arch = isnothing(grid) ? CPU() : architecture(grid))
```

Returns a wall stress model for LES simulation with default parameters similar to that proposed in [SCHUMANN1975376](@citet), [HARTEL1996283](@citet), [Piomelli1989](@citet), and [taylor2007](@citet).

Friction velocities will be precomputed at `precompute_speeds` if  `precomputed_friction_velocities` is true and `grid` is provided.

# Keyword Arguments

  * `von_Karman_constant`: the von Karman wall stress constant
  * `kinematic_viscosity`: kinematic viscosity of the water above the wall
  * `B`: wall stress constant
  * `precomputed_friction_velocities`: precompute friction velocities?
  * `precompute_speeds`: bottom water speeds to precompute friction velocities for,  this should encompas the range of speeds possible in your simulation
  * `grid`: the grid to precompute the friction velocities for
  * `arch`: architecture to adapt precomputed friction velocities for

# Example

```jldoctest
julia> using Walrus: WallStress

julia> using Oceananigans

julia> wall_stress = WallStress()
(::WallStress{Float64, Nothing}) (generic function with 1 method)
julia> boundary_conditions = (u = FieldBoundaryConditions(bottom = FluxBoundaryCondition(wall_stress, discrete_form = true, parameters = Val(:x))),
                              v = FieldBoundaryConditions(bottom = FluxBoundaryCondition(wall_stress, discrete_form = true, parameters = Val(:y))))
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
