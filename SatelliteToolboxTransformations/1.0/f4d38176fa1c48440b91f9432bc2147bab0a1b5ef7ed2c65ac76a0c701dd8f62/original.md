```
geodetic_to_geocentric(geodetic_state::AbstractVector; ellipsoid::Ellipsoid{T} = WGS84_ELLIPSOID) where T<:Number -> T, T
```

Compute the geocentric latitude and radius from the geodetic latitude `ϕ_gd` (-π/2, π/2) [rad] and height above the reference ellipsoid `h` [m] (defaults to WGS-84).  Notice that the longitude is the same in both geocentric and geodetic coordinates.

!!! info
    The longitude is the same between states so the geocentric state vector only includes latitude and radius.

    The algorithm is based in **[1]**(p. 3).


# Returns

  * `T`: Geocentric latitude [rad].
  * `T`: Radius from the center of the Earth [m].

# References

  * **[1]** ISO TC 20/SC 14 N (2011). Geomagnetic Reference Models.
