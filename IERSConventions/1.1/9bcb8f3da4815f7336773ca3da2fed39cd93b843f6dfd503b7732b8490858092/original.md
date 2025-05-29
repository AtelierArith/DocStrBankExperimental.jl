```
cip_xys(m::IERSModel, tt_c::Number, δX::Number=0, δY::Number=0)
```

Compute the CIP X, Y and CIO locator s coordinates, in radians, following the IERS  conventions `m` at time `tt_c`, expressed in `TT` Julian centuries since J2000. Optional EOP  nutation corrections can be provided via the `δX` and `δY` parameters.

!!! note
    Because of the small values of the CIP corrections, the CIO locator holds pretty much  irrespective on them. Indeed, some reports compute `s` with the corrected CIP  coordinates, some do not.


### References

  * Capitaine N. and Wallace P. T. (2008), Concise CIO based precession-nutation formulations
  * IERS Technical Note No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS Technical Note No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### See also

See also [`iers_cip_motion`](@ref) and [`cip_xy`](@ref).
