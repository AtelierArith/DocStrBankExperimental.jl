```
iers_rot3_gcrf_to_mod(tt_s::Number, m::IERSModel=iers2010b)
```

Compute the rotation matrix from the Geocentric Celestial Reference Frame (GCRF) to  the Mean-of-Date (MOD) at time `tt_s`, expressed in TT seconds since `J2000`.

!!! note
    The Mean-of-Date axes are obtained by applying the frame bias and precession matrix.  For this reason, if the [`iers1996`](@ref) conventions are used, the rotation is  actually computed starting from the MEME2000 rather than the GCRF.


### See also

See also [`iers_pb`](@ref) and [`iers_rot3_itrf_to_mod`](@ref).
