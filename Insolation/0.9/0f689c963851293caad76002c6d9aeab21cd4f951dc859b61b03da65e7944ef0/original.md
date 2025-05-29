```
instantaneous_zenith_angle(
    d::FT,
    δ::FT,
    η_UTC::FT,
    longitude::FT,
    latitude::FT,
) where {FT}
```

Returns the zenith angle (radians), azimuthal angle (radians) and Earth-Sun distance (m) at a particular longitude (degrees) and latitude (degrees) given Earth-Sun distance (m),  declination angle (radians), and hour angle (radians) at 0ᵒ longitude.
