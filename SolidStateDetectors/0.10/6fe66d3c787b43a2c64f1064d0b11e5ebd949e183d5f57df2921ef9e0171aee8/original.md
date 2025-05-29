```
mutable struct Event{T <: SSDFloat}
```

Collection struct for individual events.  This (mutable) struct is meant to be used to look at individual events, not to process a huge amount of events.

## Fields

  * `locations::VectorOfArrays{CartesianPoint{T}}`: Vector of the positions of all hits of the event.
  * `energies::VectorOfArrays{T}`: Vector of energies corresponding to the hits of the event.
  * `drift_paths::Union{Vector{EHDriftPath{T}}, Missing}`: Calculated drift paths of each hit position.
  * `waveforms::Union{Vector{<:Any}, Missing}`: Generated signals (waveforms) of the event.
