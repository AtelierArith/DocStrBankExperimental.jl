```julia
laplaceOp(V, discr)

```

For a `Galerkin` discretization, the entries of the negative laplacian are given by

$[A]_{ij} = \int_\Omega \nabla\phi_i(x) \cdot \nabla\phi_j(x) dx$

for v,u in H¹₀(Ω)

(v,-∇² u) = (vx,ux) + (vy,uy)

```
     := a(v,u)
```
