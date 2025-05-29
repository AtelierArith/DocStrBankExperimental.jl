```
kepler_to_rv(ke::KeplerianElements{Tepoch, T}) where {Tepoch <: Number, T <: Number} -> SVector{3, T}, SVector{3, T}
```

Convert the Keplerian elements `ke` to a Cartesian representation (position vector `r` [m] and velocity vector `v` [m / s]).

!!! note
    The returned vectors are represented in the same reference frame as the Keplerian elements.


# Returns

  * `SVector{3, T}`: The position vector represented in the inertial reference frame [m].
  * `SVector{3, T}`: The velocity vector represented in the inertial reference frame [m].

# Remarks

This algorithm was adapted from **[1]** and **[2]**(p. 37-38).

# References

  * **[1]**: Schwarz, R (2014). Memorandum No. 2: Cartesian State Vectors to Keplerian Orbit   Elements. Available at www.rene-schwarz.com.
  * **[2]**: Kuga, H. K., Carrara, V., Rao, K. R (2005). Introdução à Mecânica Orbital. 2ª ed.   Instituto Nacional de Pesquisas Espaciais.
