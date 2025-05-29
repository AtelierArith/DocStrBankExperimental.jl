```
selecteph2jld2(sseph::TaylorInterpolant, bodyind::T, tspan::S) where {T <: AbstractVector{Int}, S <: Number}
```

Save the ephemeris, contained in `sseph`, of the bodies with indices `bodyind`, in a `.jld2` file named as follows

```
"sseph" * number of asteroids in sseph * "ast" * number of asteroids to be saved in file * "_"
* "p" / "m" (forward / backward integration) * number of years in sseph *  "y_et.jld2"
```

# Arguments

  * `sseph::TaylorInterpolant`: ephemeris of all the bodies.
  * `bodyind::T`: indices of the bodies to be saved.
  * `tspan::S`: time span of the integration (positive -> forward integration / negative -> backward integration).
