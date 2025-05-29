```
nutation_eo_iau2006(jd_tt::Number) -> NTuple{4, Float64}
```

Compute the nutation parameters and the Equation of Origins (EO) at the Julian Day `jd_tt` [TT] using the equinox-based 2006 IAU Theory of Nutation. Notice that one can provide corrections for the nutation in obliquity (`δΔϵ_2000`) [rad] and in longitude (`δΔψ_2000`) [rad] that are usually obtained from IERS EOP Data (see [`fetch_iers_eop`](@ref)).

# Returns

  * `Float64`: The mean obliquity of the ecliptic [rad].
  * `Float64`: The nutation in obliquity of the ecliptic [rad].
  * `Float64`: The nutation in longitude [rad].
  * `Float64`: The Equation of Origins (EO) [rad].
