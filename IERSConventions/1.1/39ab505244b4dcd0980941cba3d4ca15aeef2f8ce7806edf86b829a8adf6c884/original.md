```
cip_xy(m::IERSModel, tt_c::Number)
```

Compute the CIP X and Y coordinates, in radians, following the IERS Conventions `m`, at  time `tt_c`, expressed in `TT` Julian centuries since J2000.

!!! warning
    The computation of the free-core nutation and time dependent effects are excluded from  this model. To achieve the < 1μas accuracy with the IAU 2006/2000 A precession-nutation  models, such effects must be included a-posteriori (through δX and δY) using the IERS  EOP data.


### References

  * Capitaine N. and Wallace P. T. (2008), Concise CIO based precession-nutation formulations.
  * IERS Technical Note No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS Technical Note No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### See also

See also [`iers_cip_motion`](@ref) and [`cip_xys`](@ref).
