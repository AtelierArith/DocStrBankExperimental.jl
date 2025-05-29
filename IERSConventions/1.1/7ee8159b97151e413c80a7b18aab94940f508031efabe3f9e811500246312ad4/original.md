```
iers_era(m::IERSModel, ut1_d::Number)
```

Compute the Earth Rotation Angle (ERA), in radians, at time `ut1_d` expressed as UT1 days  since `J2000`, according to the IERS convention `m`.

!!! note
    In the IERS 1996 conventions, θ is referred to as the Stellar Angle.


### References

  * IERS Technical Note No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### See also

See also [`iers_era_rotm`](@ref).
