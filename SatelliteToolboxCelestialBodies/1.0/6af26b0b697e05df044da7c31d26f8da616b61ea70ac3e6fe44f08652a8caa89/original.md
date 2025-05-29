```
moon_position_mod(jd_tdb::Number[, model]) -> SVector{3, Float64}
moon_position_mod(date_tdb::DateTime[, model]) -> SVector{3, Float64}
```

Compute the Moon position represented in the IAU-76/FK5 MOD (mean-equator, mean-equinox of date) at the Julian Day `jd_tdb` or `date_tdb`. The input time must be represented in the Barycentric Dynamical Time (TDB).

The `model` must be `Val(:Meeus)` or `Val(:Vallado)`. `Val(:Meeus)` uses the algorithm in **[2, p. 337]** that provides an accuracy of 10" in the longitude and 4" in the latitude (the reference does not mention the timespan). `Val(:Vallado)` uses the algorithm in **[1, p. 288]** that is 10x faster than `Val(:Meeus)` but can lead to errors of 0.3° in longitude and 0.2° in latitude.

!!! note
    This function performs all the computations using `Float64` due to the necessary precision.


# References

  * **[1]** Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. 4th ed.   Microcosm Press, Hawthorne, CA.
  * **[2]** Meeus, J (1998). Astronomical algorithms. Willmann-Bell, Inc, Richmond, VA.
