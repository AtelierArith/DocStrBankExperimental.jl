```
geodetic_to_ecef(lat::Number, lon::Number, h::Number; ellipsoid::Ellipsoid{T} = wgs84_ellipsoid) where T<:Number -> SVector{3, T}
```

Convert the latitude `lat` [rad], longitude `lon` [rad], and altitude `h` [m] above the reference ellipsoid (defaults to WGS-84) into a vector represented on the Earth-Centered, Earth-Fixed (ECEF) reference frame.

!!! info
    The algorithm is based in **[1]**.


# Reference

  * **[1]**: mu-blox ag (1999). Datum Transformations of GPS Positions. Application Note.
