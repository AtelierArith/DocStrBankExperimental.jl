```
rotate = Rotate(pitch, roll, yaw, spins)
```

# Arguments

  * `pitch`: (`::Real`, `[º]`) rotation in x
  * `roll`: (`::Real`, `[º]`) rotation in y
  * `yaw`: (`::Real`, `[º]`) rotation in z
  * `time`: (`::TimeCurve{T<:Real}`) time information about the motion
  * `spins`: (`::AbstractSpinSpan`) spin indexes affected by the motion

# Returns

  * `rotate`: (`::Motion`) Motion struct with [`Rotate`](@ref) action

# Examples

```julia-repl
julia> rotate = Rotate(15.0, 0.0, 20.0, TimeRange(0.0, 1.0), SpinRange(1:10))
```
