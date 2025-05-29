```
iers_rot3_gcrf_to_pef(tt_s::Number, m::IERSModel=iers2010b)
```

Compute the rotation matrix from the Geocentric Celestial Reference Frame (GCRF) to  the Pseudo-Earth Fixed (PEF) at time `tt_s`, expressed in TT seconds since `J2000`.

!!! note
    If the [`iers1996`](@ref) conventions are used, the rotation is actually computed  starting from the MEME2000 rather than the GCRF.


!!! note
    The EOP nutation corrections are only used for the [`iers2003a`](@ref) and  [`iers2010a`](@ref) models.


!!! note
    For the [`iers1996`](@ref) and [`CPNd`](@ref) models, there are no differences  between the PEF and GTOD axes. # TODO: specify the magnitude of the rotation!


## See also

See also [`iers_rot3_gcrf_to_gtod`](@ref) and [`iers_rot3_itrf_to_pef`](@ref).
