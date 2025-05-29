```
iers_gast(m::IERSModel, tt_c::Number, δΔψ::Number=0)
```

Compute the Greenwich Apparent Sidereal Time (GAST), in radians, following the IERS  Conventions `m` at time `tt_c` expressed as `TT` Julian centuries since J2000. An optional EOP  correction for the nutation in longitude can be passed via `δΔψ` for the exact computation  of the equation of the equinoxes. 

!!! note
    The input time is automatically converted to UT1 for the computation of the Earth  Rotation Angle (ERA) or for the computation of the GMST of the 1996 conventions. Thus,  EOP data must be loaded before calling this function.


### References

  * IERS Technical Note No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS Technical Note No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### See also

See also [`iers_gmst`](@ref), [`equation_equinoxes`](@ref) and [`iers_era`](@ref).
