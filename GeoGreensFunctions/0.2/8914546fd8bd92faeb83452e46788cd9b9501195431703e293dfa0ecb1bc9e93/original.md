```
_disp_vol_tet4(quadrature::Q,
    x1::R, x2::R, x3::R, A::U, B::U, C::U, D::U,
    e11::R, e12::R, e13::R, e22::R, e23::R, e33::R, nu::R
    ) where {R, U, Q}
```

Compute displacement arisen from inelastic strain in Tet4 elements.     Please see [original version](https://bitbucket.org/sbarbot/bssa-2018058/src/default/)     for complete details, especially the **coordinate system** used here.

## Arguments

  * `quadrature`: quadrature rule for integration, see   [FastGaussQuadrature.jl](https://github.com/JuliaApproximation/FastGaussQuadrature.jl)
  * `x1`, `x2`, `x3`: observational position, where $x_{3} ≥ 0$
  * `A`, `B`, `C`, `D`: a list of 3 numbers for each, each of which represents   coordinates of the vertex. All depth coordinates must be greater or   equal to 0 (no checking is performed here)
  * `e**`: strain components, each is $ϵ_{11}$, $ϵ_{12}$, $ϵ_{13}$,   $ϵ_{22}$, $ϵ_{23}$, $ϵ_{33}$
  * `nu`: poisson ratio

## Output

A vector of 3 numbers, each represents $u_{1}$, $u_{2}$, $u_{3}$

## Notice

  * Inplace version: `_disp_vol_tet4!(u, args...)` where u is a vector of 3 numbers.
