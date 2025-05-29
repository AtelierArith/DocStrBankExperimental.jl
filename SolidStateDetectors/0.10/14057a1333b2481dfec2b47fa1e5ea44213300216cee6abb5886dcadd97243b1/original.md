```
get_electron_and_hole_contribution(evt::Event{T}, sim::Simulation{T}, contact_id::Int)
```

Returns the electron and hole contribution to the waveform of a [`Contact`](@ref) with a given `contact_id` of an [`Event`](@ref) as a `NamedTuple` with two entries:  `electron_contribution` and `hole_contribution`.

## Arguments

  * `evt::Event{T}`: [`Event`](@ref) in which the charges have already been drifted.
  * `sim::Simulation{T}`: [`Simulation`](@ref) which defines the setup in which the charges in `evt` were drifted.
  * `contact_id::Int`: The `id` of the [`Contact`](@ref) for which the waveform should be split into electron and hole contribution.

## Example

```julia
using Plots
using SolidStateDetector
T = Float32

simulation = Simulation{T}(SSD_examples[:InvertedCoax])
simulate!(simulation)
event = Event([CartesianPoint{T}(0.02,0.01,0.05)])
simulate!(event, simulation)

contact_id = 1
wf = get_electron_and_hole_contribution(evt, sim, contact_id)
```

!!! note
    The drift paths in `evt` need to be calculated using [`drift_charges!`](@ref) before calling this function.


See also [`plot_electron_and_hole_contribution`](@ref).
