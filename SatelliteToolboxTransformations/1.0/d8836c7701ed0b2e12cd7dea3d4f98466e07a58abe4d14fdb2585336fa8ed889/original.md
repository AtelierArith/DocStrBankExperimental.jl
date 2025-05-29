```
ecef_to_geodetic(r_e::AbstractVector; ellipsoid::Ellipsoid{T} = WGS84_ELLIPSOID) where T<:Number -> NTuple{3, T}
```

Convert the vector `r_e` [m] represented in the Earth-Centered, Earth-Fixed (ECEF) reference frame into Geodetic coordinates for a custom target ellipsoid (defaults to WGS-84).

!!! info
    The algorithm is based in **[1]**.


# Returns

  * `T`: Latitude [rad].
  * `T`: Longitude [rad].
  * `T`: Altitude [m].

# Reference

  * **[1]**: mu-blox ag (1999). Datum Transformations of GPS Positions. Application Note.
