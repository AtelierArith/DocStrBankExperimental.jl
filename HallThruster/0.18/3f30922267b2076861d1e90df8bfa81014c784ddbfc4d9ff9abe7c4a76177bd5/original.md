```julia
run_simulation(
    config::HallThruster.Config,
    sim::HallThruster.SimParams;
    postprocess,
    restart,
    kwargs...
) -> HallThruster.Solution{_A, P, C} where {_A, P<:NamedTuple, C<:HallThruster.Config}

```

Run a Hall thruster simulation using the provided `Config` and `SimParams` objects. Returns a `Solution` object.

## Arguments

  * `config::Config`: contains geometry, plasma properties, and numerical information about the simulation. See [Configuration](@ref) for more information.
  * `sim::SimParams`: contains grid generation and timestepping information. See [Simulations](@ref) for more information.
  * `postprocess::Union{Postprocess, Nothing}`: contains file to which output is to be written and specifies what kind of output to write. If `nothing`, no output is written to file. See [Postprocessing](@ref) for more information.
  * `restart`::String:An optional path to a JSON file containing plasma data. If non-empty, the solution will be restarted from that file.
