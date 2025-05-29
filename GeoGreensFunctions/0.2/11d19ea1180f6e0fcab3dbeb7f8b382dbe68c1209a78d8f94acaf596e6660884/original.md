```
stress_tri3_hs(X::T, Y::T, Z::T, P1::V, P2::V, P3::V, Ss::T, Ds::T, Ts::T, λ::T, μ::T) where {T, V}
```

Compute stress risen from triangular dislocation in elastic *halfspace*.     Please see [original version (in supporting information)](https://academic.oup.com/gji/article/201/2/1119/572006#86405752)     for details, especially the **coordinate system** used here.

## Arguments

  * `X`, `Y`, `Z`: observational coordinates
  * `P1`, `P2`, `P3`: three triangular vertices coordinates respectively
  * `Ss`, `Ds`, `Ts`: triangular dislocation vector, Strike-slip, Dip-slip, Tensile-slip respectively
  * `λ`: Lamé's first parameter
  * `μ`: shear modulus

## Output

By order: $σ_{xx}$, $σ_{yy}$, $σ_{zz}$,     $σ_{xy}$, $σ_{xz}$, $σ_{yz}$.
