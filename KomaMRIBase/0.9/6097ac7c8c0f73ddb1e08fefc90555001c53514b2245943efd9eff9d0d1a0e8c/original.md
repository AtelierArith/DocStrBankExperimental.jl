```
heartbeat = HeartBeat(circumferential_strain, radial_strain, longitudinal_strainl, time, spins)
```

# Arguments

  * `circumferential_strain`: (`::Real`) contraction parameter
  * `radial_strain`: (`::Real`) contraction parameter
  * `longitudinal_strain`: (`::Real`) contraction parameter
  * `time`: (`::TimeCurve{T<:Real}`) time information about the motion
  * `spins`: (`::AbstractSpinSpan`) spin indexes affected by the motion

# Returns

  * `heartbeat`: (`::Motion`) Motion struct with [`HeartBeat`](@ref) action

# Examples

```julia-repl
julia> heartbeat = HeartBeat(-0.3, -0.2, 0.0, TimeRange(0.0, 1.0), SpinRange(1:10))
```
