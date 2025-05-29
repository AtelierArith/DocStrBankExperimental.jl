```
semidiscretize(semi, tspan; reset_threads=true)
```

Create an `ODEProblem` from the semidiscretization with the specified `tspan`.

# Arguments

  * `semi`: A [`Semidiscretization`](@ref) holding the systems involved in the simulation.
  * `tspan`: The time span over which the simulation will be run.

# Keywords

  * `reset_threads`: A boolean flag to reset Polyester.jl threads before the simulation (default: `true`). After an error within a threaded loop, threading might be disabled. Resetting the threads before the simulation ensures that threading is enabled again for the simulation. See also [trixi-framework/Trixi.jl#1583](https://github.com/trixi-framework/Trixi.jl/issues/1583).

# Returns

A `DynamicalODEProblem` (see [the OrdinaryDiffEq.jl docs](https://docs.sciml.ai/DiffEqDocs/stable/types/dynamical_types/)) to be integrated with [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl). Note that this is not a true `DynamicalODEProblem` where the acceleration does not depend on the velocity. Therefore, not all integrators designed for `DynamicalODEProblem`s will work properly. However, all integrators designed for `ODEProblem`s can be used. See [time integration](@ref time_integration) for more details.

# Examples

```jldoctest; output = false, filter = r"u0: .*", setup = :(trixi_include(@__MODULE__, joinpath(examples_dir(), "fluid", "hydrostatic_water_column_2d.jl"), sol=nothing); ref_system = fluid_system)
semi = Semidiscretization(fluid_system, boundary_system)
tspan = (0.0, 1.0)
ode_problem = semidiscretize(semi, tspan)

# output
ODEProblem with uType RecursiveArrayTools.ArrayPartition{Float64, Tuple{Vector{Float64}, Vector{Float64}}} and tType Float64. In-place: true
Non-trivial mass matrix: false
timespan: (0.0, 1.0)
u0: ([...], [...]) *this line is ignored by filter*
```
