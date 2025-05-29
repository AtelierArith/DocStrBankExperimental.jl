```
_stress_vol_hex8(
    x1::R, x2::R, x3::R, q1::R, q2::R, q3::R,
    L::R, T::R, W::R, theta::R,
    epsv11p::R, epsv12p::R, epsv13p::R, epsv22p::R, epsv23p::R, epsv33p::R,
    G::R, nu::R,
    ) where R
```

Compute stress arisen from inelastic strain in Hex8 elements.     Please see [original version](https://bitbucket.org/sbarbot/bssa-2016237/src/master/)     for complete details, especially the **coordinate system** used here.

## Arguments

The same as [`_disp_vol_hex8`](@ref)

## Output

A vector of 6 numbers, each represents $σ_{11}$, $σ_{12}$, $σ_{13}$,     $σ_{22}$, $σ_{23}$, $σ_{33}$

## Notice

  * Inplace version: `_stress_vol_hex8!(u, args...)` where u is a vector of 6 numbers.
