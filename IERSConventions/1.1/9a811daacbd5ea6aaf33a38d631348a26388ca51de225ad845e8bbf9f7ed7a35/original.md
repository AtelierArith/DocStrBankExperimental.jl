```
iers_rot3_gcrf_to_gtod(tt_s::Number, m::IERSModel=iers2010b)
```

Compute the rotation matrix from the Geocentric Celestial Reference Frame (GCRF) to  the Greenwich True-of-Date (GTOD) at time `tt_s`, expressed in TT seconds since `J2000`.

!!! note
    If the [`iers1996`](@ref) conventions are used, the rotation is actually computed  starting from the MEME2000 rather than the GCRF.


!!! note
    The EOP nutation corrections are only used for the [`iers2003a`](@ref) and  [`iers2010a`](@ref) models.


## See also

See also [`iers_rot3_itrf_to_gtod`](@ref).
