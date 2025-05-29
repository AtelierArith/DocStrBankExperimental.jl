```
path = Path(dx, dy, dz, time, spins)
```

# Arguments

  * `dx`: (`::AbstractArray{T<:Real}`, `[m]`) displacements in x
  * `dy`: (`::AbstractArray{T<:Real}`, `[m]`) displacements in y
  * `dz`: (`::AbstractArray{T<:Real}`, `[m]`) displacements in z
  * `time`: (`::TimeCurve{T<:Real}`) time information about the motion
  * `spins`: (`::AbstractSpinSpan`) spin indexes affected by the motion

# Returns

  * `path`: (`::Motion`) Motion struct with [`Path`](@ref) action

# Examples

```julia-repl
julia> path = Path(
          [0.01 0.02; 0.02 0.03], 
          [0.02 0.03; 0.03 0.04], 
          [0.03 0.04; 0.04 0.05], 
          TimeRange(0.0, 1.0), 
          SpinRange(1:10)
       )
```
