```
iers_rot3_itrf_to_pef(tt_s::Number, m::IERSModel=iers2010b)
```

Compute the rotation matrix from the International Terrestrial Reference Frame (ITRF) to  the Pseudo-Earth Fixed (PEF) at time `tt_s`, expressed in TT seconds since `J2000`.

!!! note
    The [`CPNd`](@ref) model returns an identity rotation because it neglects the  effects of polar motion. # TODO: specify magnitude!


## See also

See also [`iers_rot3_gcrf_to_pef`](@ref).
