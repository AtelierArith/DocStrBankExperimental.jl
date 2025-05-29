```
flowpath = FlowPath(dx, dy, dz, spin_reset, time, spins)
```

# Arguments

  * `dx`: (`::AbstractArray{T<:Real}`, `[m]`) displacements in x
  * `dy`: (`::AbstractArray{T<:Real}`, `[m]`) displacements in y
  * `dz`: (`::AbstractArray{T<:Real}`, `[m]`) displacements in z
  * `spin_reset`: (`::AbstractArray{Bool}`) reset spin state flags
  * `time`: (`::TimeCurve{T<:Real}`) time information about the motion
  * `spins`: (`::AbstractSpinSpan`) spin indexes affected by the motion

# Returns

  * `flowpath`: (`::Motion`) Motion struct with [`FlowPath`](@ref) action

# Examples

```julia-repl
julia> flowpath = FlowPath(
          [0.01 0.02; 0.02 0.03], 
          [0.02 0.03; 0.03 0.04], 
          [0.03 0.04; 0.04 0.05], 
          [false false; false true],
          TimeRange(0.0, 1.0), 
          SpinRange(1:10)
       )
```
