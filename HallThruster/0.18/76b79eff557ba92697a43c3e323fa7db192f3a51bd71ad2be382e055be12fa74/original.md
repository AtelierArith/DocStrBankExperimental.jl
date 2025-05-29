```julia
struct Solution{T, P, C, S}
```

The solution of a simulation, returned by `run_simulation`. These can be passed to any of the postprocessing functions described in [Postprocessing](@ref), or indexed to extract specific values.

# Indexing

There are a few ways to index a solution. First, you can extract a solution containing a single frame by indexing the `Solution` by an integer.

```jldoctest; setup = :(using HallThruster: HallThruster as het; config = het.Config(discharge_voltage = 300, thruster = het.SPT_100, anode_mass_flow_rate=5e-6, domain = (0.0, 0.08)); simparams = het.SimParams(dt = 5e-9, grid = het.EvenGrid(50), duration = 1e-3, num_save = 101, verbose=false); solution = het.run_simulation(config, simparams))
julia> solution = het.run_simulation(config, simparams)
Hall thruster solution with 101 saved frames (retcode: success, end time: 0.001 seconds)

julia> solution[51]
Hall thruster solution with 1 saved frame (retcode: success, end time: 0.0005 seconds)
```

Second, you can index a solution by a vector or vector-like object to extract a range of frames

```jldoctest; setup = :(using HallThruster: HallThruster as het; config = het.Config(discharge_voltage = 300, thruster = het.SPT_100, anode_mass_flow_rate=5e-6, domain = (0.0, 0.08)); simparams = het.SimParams(dt = 5e-9, grid = het.EvenGrid(50), duration = 1e-3, num_save = 101, verbose=false); solution = het.run_simulation(config, simparams))
julia> solution[51:end] # get last 51 frames
Hall thruster solution with 51 saved frames (retcode: success, end time: 0.001 seconds)

julia> solution[begin:2:end] # get every other frame
Hall thruster solution with 51 saved frames (retcode: success, end time: 0.001 seconds)

julia> solution[[1, 51, 101]] # get only frames 1, 51, 101
Hall thruster solution with 3 saved frames (retcode: success, end time: 0.001 seconds)
```

Lastly, you can index by a symbol or [Symbol, Integer] to get plasma data for all frames in that solution

```julia
solution[:ni, 1] 	# get ion density of first charge state for all frames
solution[:ui] 		# get ion velocity for all charge states and frames

# These return the same thing
solution[:∇pe]
solution[:grad_pe]
```

For a list of valid fields to index by, call `HallThruster.valid_fields()` For a list of alternate names for fields containing special characters, call `HallThruster.alternate_field_names()`

See the documentation for `Base.getindex(sol::Solution, field::Symbol)` and `Base.getindex(sol::Solution, field::Symbol, charge::Integer)` for more information.

# Fields

  * `t::Any`: A vector of times (in seconds) at which simulation output has been saved

  * `frames::Any`: A vector of frames, or snapshots of the simulation state, at the times specified in `t`

  * `params::Any`: The solution parameters vector. Contains auxilliary information about the simulation.

  * `config::Any`: The `Config` used to run the simulation

  * `retcode::Symbol`: The solution return code. This can be one of three values:

    1. `:success`: the simulation completed successfully.
    2. `:failure`: the simulation failed due to a numerical issue or instability, resulting in a `NaN` or `Inf being detected somewhere in the solution`
    3. `:error`: another error occurred. Check the `error` string to see what kind of error.

  * `error::String`: Holds to error text and backtrace, if an error occurred. Empty if `sol.retcode != :error`.
