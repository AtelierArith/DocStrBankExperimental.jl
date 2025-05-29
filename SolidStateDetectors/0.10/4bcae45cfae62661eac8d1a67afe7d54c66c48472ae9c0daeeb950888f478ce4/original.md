```
simulate!(evt::Event{T}, sim::Simulation{T}; kwargs...)::Nothing where {T <: SSDFloat}
```

Simulates the waveforms for the [`Event`](@ref) for a given [`Simulation`](@ref) by

1. calculating the drift paths of all energy hits, at `evt.locations` and
2. generating the waveforms for each [`Contact`](@ref), for which a [`WeightingPotential`](@ref) is specified in `sim.weighting_potentials`.

The output is stored in `evt.drift_paths` and `evt.waveforms`.

## Arguments

  * `evt::Event{T}`: [`Event`](@ref) for which the charges should be drifted.
  * `sim::Simulation{T}`: [`Simulation`](@ref) which defines the setup in which the charges in `evt` should drift.

## Keywords

  * `max_nsteps::Int = 1000`: Maximum number of steps in the drift of each hit.
  * `Δt::RealQuantity = 5u"ns"`: Time step used for the drift.
  * `diffusion::Bool = false`: Activate or deactive diffusion of charge carriers via random walk.
  * `self_repulsion::Bool = false`: Activate or deactive self-repulsion of charge carriers of the same type.
  * `verbose = true`: Activate or deactivate additional info output.

## Example

```julia
simulate!(evt, sim, Δt = 1u"ns", verbose = false)
```

See also [`drift_charges!`](@ref) and [`get_signals!`](@ref).
