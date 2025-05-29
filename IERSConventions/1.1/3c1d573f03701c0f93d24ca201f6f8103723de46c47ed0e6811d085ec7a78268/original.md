```
iers_npb(m::IERSModel, tt_c::Number, δΔψ=0, δΔϵ=0)
```

Compute the nutation-bias-precession (NPB) matrix, which transforms vectors from the GCRF  to True-of-Date (TOD) axes, at time `tt_c` expressed in `TT` Julian centuries since `J2000`,  according to the IERS convention `m`

### References

  * Wallace P. T. and Capitaine N. (2006), Precession-nutation procedures consistent with  IAU 2006 resolutions, [DOI: 10.1051/0004-6361:20065897](https://www.aanda.org/articles/aa/abs/2006/45/aa5897-06/aa5897-06.html)
  * IERS Technical Note No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS Technical Note No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### See also

See also [`iers_nutation`](@ref), [`iers_precession`](@ref) and [`iers_pb`](@ref).
