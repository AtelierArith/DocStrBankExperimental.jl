```
d_dt(p::Abstract1DProfile)
```

Take the time derivative of `p` and return it as a new profile.

# Example

```jldoctest
julia> s = SpaceTimeFields.Sinusoid(π)
Sinusoid (ω = 3.14)

julia> s.([0.0, 0.5, 0.75])
3-element Array{Float64,1}:
 0.0
 1.0
 0.707107

julia> c = SpaceTimeFields.d_dt(s)
d/dt (Sinusoid (ω = 3.14))

julia> c.([0.0, 0.5, 0.75])
3-element Array{Float64,1}:
  3.14159
  1.92367e-16
 -2.22144
```
