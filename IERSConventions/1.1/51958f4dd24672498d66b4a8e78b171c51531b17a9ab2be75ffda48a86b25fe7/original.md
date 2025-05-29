```
iers_cip_motion(m::IERSModel, tt_c::Number, δX::Number=0, δY::Number=0)
```

Compute the GCRF-to-CIRF rotation matrix, following the IERS Conventions `m`, at time `tt_c`  expressed in `TT` Julian centuries since J2000. Optional IERS EOP corrections for free-core  nutation and time dependent effects can be provided via `δX` and `δY`

### References

  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### See also

See also [`cip_xy`](@ref) and [`cip_xys`](@ref).
