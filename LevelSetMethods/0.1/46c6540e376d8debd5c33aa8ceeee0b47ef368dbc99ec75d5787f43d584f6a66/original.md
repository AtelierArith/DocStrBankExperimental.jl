```
LevelSetEquation(; terms, levelset, boundary_conditions, t = 0, integrator = RK3())
```

Create a of a level-set equation of the form `ϕₜ + sum(terms) = 0`, where each `t ∈ terms` is a [`LevelSetTerm`](@ref) and `levelset` is the initial [`LevelSet`](@ref).

Calling [`integrate!(ls, tf)`](@ref) will evolve the level-set equation up to time `tf`, modifying the `current_state(eq)` and `current_time(eq)` of the object `eq` in the process (and therefore the original `levelset`).

Boundary conditions can be specified in two ways. If a single `BoundaryCondition` is provided, it will be applied uniformly to all boundaries of the domain. To apply different boundary conditions to each boundary, pass a tuple of the form `(bc_x, bc_y, ...)` with as many elements as dimensions in the domain. If `bc_x` is a `BoundaryCondition`, it will be applied to both boundaries in the `x` direction. If `bc_x` is a tuple of two `BoundaryCondition`s, the first will be applied to the left boundary and the second to the right boundary. The same logic applies to the other dimensions.

The optional parameter `t` specifies the initial time of the simulation, and `integrator` is the [`TimeIntegrator`](@ref) used to evolve the level-set equation.

```jldoctest; output = true
using LevelSetMethods, StaticArrays
grid = CartesianGrid((-1, -1), (1, 1), (50, 50))    # define the grid
ϕ = LevelSet(x -> x[1]^2 + x[2]^2 - 0.5^2, grid)    # initial shape
𝐮 = MeshField(x -> SVector(1, 0), grid)             # advection velocity
terms = (AdvectionTerm(𝐮),)            # advection and curvature terms
bc = PeriodicBC()                                   # periodic boundary conditions
eq = LevelSetEquation(; terms, levelset = ϕ, bc)    # level-set equation

# output

Level-set equation given by

 	 ϕₜ + 𝐮 ⋅ ∇ ϕ = 0

Current time 0.0

```
