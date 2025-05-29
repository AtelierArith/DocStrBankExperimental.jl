```
compute_δϵ_δψ(eop_iau2000a::EopIau2000A, JD::Number) -> (Float64, Float64)
```

Compute the celestial pole offsets in obliquity (`δΔϵ_2000`) and longitude (`δΔΨ_2000`) [arcsec] given the IERS EOP IAU 2000A `eop_iau2000a`.

This function obtains those values by converting the celestial pole offsets with respect to the GCRS (`δx` and `δy`). These values are necessary in the equinox-based IAU-2006 theory.

The algorithm was obtained from **[1]**(eq. 5.25) and **[2]**(`DPSIDEPS2000_DXDY2000`).

# References

  * **[1]**: IERS (2010). Transformation between the International Terrestrial Reference   System and the Geocentric Celestial Reference System. IERS Technical Note No. 36,   Chapter 5.
  * **[2]**: ftp://hpiers.obspm.fr/eop-pc/models/uai2000.package
