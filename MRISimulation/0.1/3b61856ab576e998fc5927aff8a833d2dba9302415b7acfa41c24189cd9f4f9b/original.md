```
epgRotation(alpha::Float64, F::Vector{T}, Z::Vector{T}; statesConsidered=nothing, phi::Float64=0.0)
```

applies Bloch-rotation (<=> RF pulse) to a set of EPG states.

# Arguments

  * `alpha::Float64`           - flip angle of the RF pulse
  * `F::Vector{T}`             - transverse dephasing stats
  * `Z::Vector{T}`             - longitudinal dephasing stats
  * `statesConsidered=nothing` - number of dephasing states to consider (nothing means all states are taken into account)
  * `phi::Float64=0.0`         - phase of the RF pulse
