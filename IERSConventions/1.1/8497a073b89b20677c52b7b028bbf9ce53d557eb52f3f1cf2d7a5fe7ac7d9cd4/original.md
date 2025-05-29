```
iers_rot3_gcrf_to_itrf(tt_s::Number, m::IERSModel=iers2010b)
```

Compute the rotation matrix from the Geocentric Celestial Reference Frame (GCRF) to  the International Terrestrial Reference Frame (ITRF) at time `tt_s`, expressed in TT seconds  since `J2000`, following the IERS Conventions `m`. 

!!! note
    EOP corrections to the CIP coordinates (δX, δY) are only added in the [`iers2003a`](@ref) and [`iers2010a`](@ref) models.


!!! note
    Polar motion is neglected in the [`CPNd`](@ref) model.


### References

  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### See also

See also [`iers_rot3_gcrf_to_cirf`](@ref) and [`iers_rot3_gcrf_to_tirf`](@ref).
