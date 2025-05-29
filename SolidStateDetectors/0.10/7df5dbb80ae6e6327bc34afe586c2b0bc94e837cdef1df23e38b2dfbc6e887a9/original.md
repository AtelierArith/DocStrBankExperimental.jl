```
simulate_waveforms( mcevents::TypedTables.Table, sim::Simulation{T}; kwargs...)
simulate_waveforms( mcevents::TypedTables.Table, sim::Simulation{T}, output_dir::AbstractString, output_base_name::AbstractString; kwargs...)
```

Simulates the waveforms for all events defined in `mcevents` for a given [`Simulation`](@ref) by

1. calculating the drift paths of all energy hits defined in `mcevents`,
2. determining the signal (waveforms) for each [`Contact`](@ref),   for which a [`WeightingPotential`](@ref) is specified in `sim.weighting_potentials`.

## Arguments

  * `mcevents::TypedTables.Table`: Table with information about events in the simulated setup.
  * `sim::Simulation{T}`: [`Simulation`](@ref) which defines the setup in which the charges in `mcevents` should drift.

If [LegendHDF5IO.jl](https://github.com/legend-exp/LegendHDF5IO.jl) is loaded, this function has additional arguments. 

## Additional Arguments (`LegendHDF5IO`)

  * `output_dir::AbstractString`: Directory where the HDF5 output file is saved.
  * `output_base_name::AbstractString`: Basename of the HDF5 output file, default is `"generated_waveforms"`.

## Keywords

  * `max_nsteps::Int = 1000`: Maximum number of steps in the drift of each hit.
  * `Δt::RealQuantity = 4u"ns"`: Time step used for the drift.
  * `diffusion::Bool = false`: Activate or deactive diffusion of charge carriers via random walk.
  * `self_repulsion::Bool = false`: Activate or deactive self-repulsion of charge carriers of the same type.
  * `number_of_carriers::Int = 1`: Number of charge carriers to be used in the N-Body simulation of an energy deposition.
  * `number_of_shells::Int = 1`: Number of shells around the `center` point of the energy deposition.
  * `max_interaction_distance = NaN`: Maximum distance for which charge clouds will interact with each other (if `NaN`, then all charge clouds drift independently).
  * `verbose = false`: Activate or deactivate additional info output.
  * `chunk_n_physics_events::Int = 1000` (`LegendHDF5IO` only): Number of events that should be saved in a single HDF5 output file.

## Examples

```julia
simulate_waveforms(mcevents, sim, Δt = 1u"ns", verbose = false)
# => returns the input table `mcevents` with an additional column `waveform` in which the generated waveforms are stored
```

```julia
using LegendHDF5IO
simulate_waveforms(mcevents, sim, "output_dir", "my_basename", Δt = 1u"ns", verbose = false)
# => simulates the charge drift and saves the output to "output_dir/my_basename_evts_xx.h5"
```

!!! note
    The drift paths are just calculated temporarily and not returned.


!!! note
    Using values with units for `Δt` requires the package [Unitful.jl](https://github.com/PainterQubits/Unitful.jl).

