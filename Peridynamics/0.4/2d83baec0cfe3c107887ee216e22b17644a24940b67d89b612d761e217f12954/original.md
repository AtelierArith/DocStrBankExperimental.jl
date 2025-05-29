```
Job(spatial_setup, time_solver; kwargs...)
```

A type that contains all the information necessary for a peridynamic simulation. You can [`submit`](@ref) a `Job` to start the simulation.

# Arguments

  * `spatial_setup`: A [`Body`](@ref) or [`MultibodySetup`](@ref).
  * `time_solver`: [`VelocityVerlet`](@ref) or [`DynamicRelaxation`](@ref).

# Keywords

  * `path::String`: Path to store results. If it does not exist yet it will be created during   the simulation. (optional)
  * `freq::Int`: Output frequency of result files. A output file will be written every   `freq`-th time step. (default: `10`)
  * `fields`: Fields that should be exported to output files. Allowed keywords depend on the   selected material model. Please look at the documentation of the material you specified   when creating the body. (default: `(:displacement, :damage)`)

    If `spatial_setup` is a **`Body`**, the `fields` keyword can be of the form:

      * `fields::Symbol`: A symbol specifying a single output field.
      * `fields::NTuple{N,Symbol} where N`: A Tuple specifying multiple output fields.
      * `fields::Vector{Symbol}`: A Vector specifying multiple output fields.

    If `spatial_setup` is a **`MultibodySetup`**, the `fields` keyword can also be specified   for every body separately:

      * `fields::Dict{Symbol,T}`: A Dictionary containing the fields separately for every   body. `T` is here every possible type of the `fields` keyword that can be used for a   single body.

!!! note "No file export"
    If no keyword is specified when creating a `Job`, then no files will be exported.


# Example

```julia-repl
julia> job = Job(multibody_setup, verlet_solver; path="my_results/sim1")
Job:
  spatial_setup  25880-point MultibodySetup
  time_solver    VelocityVerlet(n_steps=2000, safety_factor=0.7)
  options        export_allowed=true, freq=10
```
