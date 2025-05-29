```
cip_vector(m::IERSModel, tt_c::Number)
```

Compute the Celestial Intermediate Pole (CIP) vector, following the IERS Conventions `m` at  time `tt_c`, expressed in `TT` Julian centuries since J2000.

### References

  * Wallace P. T. and Capitaine N. (2006), Precession-nutation procedures consistent with  IAU 2006 resolutions, [DOI: 10.1051/0004-6361:20065897](https://www.aanda.org/articles/aa/abs/2006/45/aa5897-06/aa5897-06.html)

### See also

See also [`cip_xy`](@ref).
