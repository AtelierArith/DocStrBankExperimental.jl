```
iers_nutation_comp(m::IERSModel, tt_c::Number)
```

Compute the nutation components in longitude and obliquity for the IERS convention `m`, in  radians, at time `tt_c` expressed in `TT` Julian Centuries since `J2000`.

!!! note
    For the **IAU 2006A** model, the function strictly follows the SOFA implementation. It  first computes the IAU 2000A nutation, then applies adjustments for the consequences of  the change in obliquity from the IAU 1980 ecliptic to the IAU 2006 ecliptic and (ii)  for the secular variation in the Earth's dynamical form factor J2. These corrections  ensure that the IAU 2000A nutation is consistent with the IAU 2006 precession model.  Please note that the coefficients available on the IERS tables already include those  corrections, and are retrieved by multiplying the amplitudes of the SOFA nutation in  longitude coefficients by 1.00000047.


!!! note
    The expressions of these components for the [`CPNc`](@ref) and [`CPNd`](@ref) models are  indirectly computed from their CIP series expansion.


!!! warning
    The computation of the free-core nutation and time dependent effects are excluded from  this model. To achieve the < 1μas accuracy with the IAU 2006/2000 A precession-nutation  models, such effects must be included a-posteriori (through δΔψ and δΔϵ) using the IERS  EOP data.


### References

  * IERS Technical Note No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS Technical Note No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)
  * Wallace P. T. and Capitaine N. (2006), Precession-nutation procedures consistent with  IAU 2006 resolutions, [DOI: 10.1051/0004-6361:20065897](https://www.aanda.org/articles/aa/abs/2006/45/aa5897-06/aa5897-06.html)
  * Capitaine N. and Wallace P. T. (2008), Concise CIO based precession-nutation formulations
  * ERFA [nut06a](https://github.com/liberfa/erfa/blob/master/src/nut06a.c) and  [nut00b](https://github.com/liberfa/erfa/blob/master/src/nut00b.c) functions

### See also

See also [`iers_nutation`](@ref)
