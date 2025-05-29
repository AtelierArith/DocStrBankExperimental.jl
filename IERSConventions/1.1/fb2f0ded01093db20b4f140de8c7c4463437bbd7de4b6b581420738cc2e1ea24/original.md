```
iers_polar_motion(m::IERSModel, xₚ::Number, yₚ::Number, tt_c::Number)
```

Compute the Polar Motion TIRF-to-ITRF rotation matrix, according to the IERS Conventions  `m`, at time `tt_c` expressed in `TT` Julian centuries since `J2000`. The function requires  `xp` and `yp`, the Celestial Intermediate Pole (CIP) coordinates with respect to the  International Celestial Reference Frame (ITFR).

# TODO: expand description! (and check assumption for CPNd)

### References

  * IERS Technical Note No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS Technical Note No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)
