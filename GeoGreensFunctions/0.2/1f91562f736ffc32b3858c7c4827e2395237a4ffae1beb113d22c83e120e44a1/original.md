```
disp_tri3_hs(X::T, Y::T, Z::T, P1::V, P2::V, P3::V, Ss::T, Ds::T, Ts::T, nu::T) where {T, V}
```

Compute displacement risen from triangular dislocation in elastic *halfspace*.     Please see [original version (in supporting information)](https://academic.oup.com/gji/article/201/2/1119/572006#86405752)     for details, especially the **coordinate system** used here.

## Arguments

  * `X`, `Y`, `Z`: observational coordinates
  * `P1`, `P2`, `P3`: three triangular vertices coordinates respectively
  * `Ss`, `Ds`, `Ts`: triangular dislocation vector, Strike-slip, Dip-slip, Tensile-slip respectively
  * `nu`: poisson ratio

## Output

By order: $u_x$, $u_y$, $u_z$
