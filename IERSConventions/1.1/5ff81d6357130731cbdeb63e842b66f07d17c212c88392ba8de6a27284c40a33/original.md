```
iers_gmst(m::IERSModel, tt_c::Number)
```

Compute the Greenwich Mean Sidereal Time (GMST), in radians, following the IERS Conventions  `m` at time `tt_c` expressed as `TT` Julian centuries since J2000. 

!!! note
    The input time is automatically converted to UT1 for the computation of the Earth  Rotation Angle (ERA) or for the computation of the GMST of the 1996 conventions. Thus,  EOP data must be loaded before calling this function.


### References

  * IERS Technical Note No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS Technical Note No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### See also

See also [`iers_gast`](@ref) and [`iers_era`](@ref).
