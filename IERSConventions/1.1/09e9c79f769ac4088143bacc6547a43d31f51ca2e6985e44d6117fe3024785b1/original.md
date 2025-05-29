```
iers_obliquity(m::IERSModel, tt_c::Number)
```

Compute the mean obliquity of the ecliptic at epoch, in radians, at time `tt_c` expressed in  `TT` Julian centuries since `J2000`, according to the IERS convention `m`.

!!! note
    The mean obliquity for the IERS 2003 conventions already accounts the adjustment to the  IAU 1976 precession model for the IAU 2000 precession-rate of the equator in obliquity .


### References

  * IERS Technical Note No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS Technical Note No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)
