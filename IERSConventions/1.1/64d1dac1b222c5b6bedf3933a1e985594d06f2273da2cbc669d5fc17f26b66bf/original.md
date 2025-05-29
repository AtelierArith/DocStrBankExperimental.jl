```
iers_rot3_itrf_to_gtod(tt_s::Number, m::IERSModel=iers2010b)
```

Compute the rotation matrix from the International Terrestrial Reference Frame (ITRF) to  the Greenwich True-of-Date (GTOD) at time `tt_s`, expressed in TT seconds since `J2000`.

!!! note
    The [`CPNd`](@ref) model returns an identity rotation because it neglects the  effects of polar motion. # TODO: specify magnitude!


!!! note
    For the [`iers1996`](@ref) model, the GTOD and PEF axes are equal because the IERS  1996 conventions do not account for the TIO locator effects.


## See also

See also [`iers_rot3_itrf_to_pef`](@ref) and [`iers_rot3_gcrf_to_gtod`](@ref).
