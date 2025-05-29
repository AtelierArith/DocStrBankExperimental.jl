```
iers_rot3_itrf_to_tod(tt_s::Number, m::IERSModel=iers2010b)
```

Compute the rotation matrix from the International Terrestrial Reference Frame (ITRF) to  the True-of-Date (TOD) at time `tt_s`, expressed in TT seconds since `J2000`.

!!! note
    The EOP corrections in longitude are only used for the [`iers2003a`](@ref) and  [`iers2010a`](@ref) models.


## See also

See also [`iers_rot3_itrf_to_gtod`](@ref) and [`iers_rot3_gcrf_to_tod`](@ref).
