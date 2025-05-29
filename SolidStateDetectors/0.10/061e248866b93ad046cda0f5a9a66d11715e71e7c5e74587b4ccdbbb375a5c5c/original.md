```
drift_charges!(evt::Event{T}, sim::Simulation{T}; kwargs...)::Nothing where {T <: SSDFloat}
```

Calculates the electron and hole drift paths for the given [`Event`](@ref) and [`Simulation`](@ref)     and stores them in `evt.drift_paths`.

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
drift_charges!(evt, sim, Δt = 1u"ns", verbose = false)
```

!!! note
    Using values with units for `Δt` requires the package [Unitful.jl](https://github.com/PainterQubits/Unitful.jl).

