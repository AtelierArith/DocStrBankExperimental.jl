```
_disp_vol_hex8(
    x1::R, x2::R, x3::R, q1::R, q2::R, q3::R,
    L::R, T::R, W::R, theta::R,
    epsv11p::R, epsv12p::R, epsv13p::R, epsv22p::R, epsv23p::R, epsv33p::R,
    G::R, nu::R,
    ) where R
```

Compute displacement arisen from inelastic strain in Hex8 elements.     Please see [original version](https://bitbucket.org/sbarbot/bssa-2016237/src/master/)     for complete details, especially the **coordinate system** used here.

## Arguments

  * `x1`, `x2`, `x3`: observational position, where $x_{3} ≥ 0$
  * `q1`, `q2`, `q3`: Hex8 element position, where $q_{3} ≥ 0$
  * `L`, `T`, `W`: Hex8 element length, thickness and width
  * `theta`: strike angle
  * `epsv**`: strain components, each is $ϵ_{11}$, $ϵ_{12}$, $ϵ_{13}$,   $ϵ_{22}$, $ϵ_{23}$, $ϵ_{33}$
  * `G`: shear modulus
  * `nu`: poisson ratio

## Output

A vector of 3 numbers, each represents $u_{1}$, $u_{2}$, $u_{3}$

## Notice

  * Inplace version: `_disp_vol_hex8!(u, args...)` where u is a vector of 3 numbers.
