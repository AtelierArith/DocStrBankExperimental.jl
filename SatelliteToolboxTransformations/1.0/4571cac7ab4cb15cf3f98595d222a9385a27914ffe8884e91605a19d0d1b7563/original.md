```
precession_fk5(jd_tt::Number) -> (Float64, Float64, Float64)
```

Compute the angles related to the precession movement in the Julian Day `jd_tt` [Terrestrial Time] using the theory IAU-76/FK5.

# Returns

  * `NTuple{3, Float64}`: The angles (ζ, Θ, z) as described in **[1]**(p. 226-228).

# References

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.
