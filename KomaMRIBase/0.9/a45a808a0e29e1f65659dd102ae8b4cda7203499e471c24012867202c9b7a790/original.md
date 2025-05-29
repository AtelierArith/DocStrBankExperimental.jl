```
translate = Translate(dx, dy, dz, time, spins)
```

# Arguments

  * `dx`: (`::Real`, `[m]`) translation in x
  * `dy`: (`::Real`, `[m]`) translation in y
  * `dz`: (`::Real`, `[m]`) translation in z
  * `time`: (`::TimeCurve{T<:Real}`) time information about the motion
  * `spins`: (`::AbstractSpinSpan`) spin indexes affected by the motion

# Returns

  * `translate`: (`::Motion`) Motion struct

# Examples

```julia-repl
julia> translate = Translate(0.01, 0.02, 0.03, TimeRange(0.0, 1.0), SpinRange(1:10))
```
