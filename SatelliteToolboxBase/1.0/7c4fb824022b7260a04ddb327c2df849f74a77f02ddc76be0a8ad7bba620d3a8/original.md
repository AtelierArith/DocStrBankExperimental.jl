```
rv_to_kepler(r_i::AbstractVector{T1}, v_i::AbstractVector{T2}, t::T3 = 0) where {T1<:Number, T2<:Number, T3<:Number} -> KeplerianElements{Tepoch, T}
```

Convert a Cartesian representation (position vector `r_i` [m] and velocity vector `v_i` [m / s]) to Keplerian elements. Optionally, the user can specify the epoch of the returned elements using the parameter `t`. It it is omitted, then it defaults to 0.

!!! note
    The output type `Tepoch` is obtained by converting `T3` to float, whereas the output type `T` is obtained by promoting `T1` and `T2` and converting the result to float.


# Returns

  * `KeplerianElements{Tepoch, T}`: The Keplerian elements [SI units].

# Remarks

The algorithm was adapted from **[1]**.

The special cases are treated as follows:

  * **Circular and equatorial**: the right ascension of the ascending node and the argument of   perigee are set to 0. Hence, the true anomaly is equal to the true longitude.
  * **Elliptical and equatorial**: the right ascension of the ascending node is set to 0.   Hence, the argument of perigee is equal to the longitude of periapsis.
  * **Circular and inclined**: the argument of perigee is set to 0. Hence, the true anomaly is   equal to the argument of latitude.

# References

  * **[1]**: Schwarz, R (2014). Memorandum No. 2: Cartesian State Vectors to Keplerian Orbit   Elements. Available at www.rene-schwarz.com.
