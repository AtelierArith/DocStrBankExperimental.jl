```
iers_nutation(m::IERSModel, tt_c::Number, δΔψ::Number=0, δΔϵ::Number=0)
```

Compute the nutation matrix that rotates a vector from Mean-of-Date (MOD) to True-of-Date  (TOD) axes following the IERS convention `m`, at time `tt_c` expressed in `TT` Julian  Centuries since `J2000`. 

Optional EOP nutation corrections can be provided via the `δΔψ` and `δΔϵ` parameters.

### References

  * Wallace P. T. and Capitaine N. (2006), Precession-nutation procedures consistent with  IAU 2006 resolutions, [DOI: 10.1051/0004-6361:20065897](https://www.aanda.org/articles/aa/abs/2006/45/aa5897-06/aa5897-06.html)

### See also

See also [`iers_nutation_comp`](@ref) and [`iers_obliquity`](@ref). 
