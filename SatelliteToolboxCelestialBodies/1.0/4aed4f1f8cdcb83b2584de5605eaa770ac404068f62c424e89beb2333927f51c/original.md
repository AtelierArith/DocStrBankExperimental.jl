```
sun_velocity_mod(jd_tdb::Number) -> SVector{3, Float64}
sun_velocity_mod(date_tdb::DateTime) -> SVector{3, Float64}
```

Compute the Sun velocity measured and represented in the IAU-76/FK5 MOD (mean-equator, mean-equinox of date) at the Julian Day `jd_tdb` or `date_tdb`. The input time must be represented in the Barycentric Dynamical Time (TDB). The algorithm was obtained by computing the time derivative of the Sun position in [1, p. 277-279].

!!! note
    This function performs all the computations using `Float64` due to the necessary precision.


# References

  * **[1]** Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. 4th ed.   Microcosm Press, Hawthorne, CA.
