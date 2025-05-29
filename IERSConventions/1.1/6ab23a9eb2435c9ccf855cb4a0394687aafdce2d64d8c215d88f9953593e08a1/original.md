```
iers_rot3_itrf_to_mod(tt_s::Number, m::IERSModel=iers2010b)
```

Compute the rotation matrix from the International Terrestrial Reference Frame (ITRF) to  the Mean-of-Date (MOD) at time `tt_s`, expressed in TT seconds since `J2000`.

!!! note
    The EOP nutation corrections are only used for the [`iers2003a`](@ref) and  [`iers2010a`](@ref) models.


## See also

See also [`iers_rot3_itrf_to_tod`](@ref) and [`iers_rot3_gcrf_to_mod`](@ref).
