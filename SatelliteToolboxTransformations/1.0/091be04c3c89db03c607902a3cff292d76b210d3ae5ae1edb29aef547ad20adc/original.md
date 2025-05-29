```
geocentric_to_geodetic(ϕ_gc::Number, r::Number; ellipsoid::Ellipsoid{T} = WGS84_ELLIPSOID) where T<:Number -> T, T
```

Compute the geodetic latitude and altitude above the reference ellipsoid (defaults to WGS-84) from the geocentric latitude `ϕ_gc` (-π/2, π/2) [rad] and radius `r` [m].  Notice that the longitude is the same in both geocentric and geodetic coordinates.

!!! info
    The algorithm is based in **[1]**.


# Returns

  * `T`: Geodetic latitude [rad].
  * `T`: Altitude above the reference ellipsoid (defaults to WGS-84) [m].

# References

  * **[1]** Borkowski, K. M (1987). Transformation of geocentric to geodetic coordinates   without approximations. Astrophysics and Space Science, vol.  139, pp. 1-4.
