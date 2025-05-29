```julia
advectionOp(vels, V, discr, Vd; ...)
advectionOp(vels, V, discr, Vd, J; vel_update_funcs)

```

`Galerkin` discretizations suppport dealiased implementation of vector calculus operations where integration is performed in  a(usually higher order) space, `Vd`. This is referred to as over-integration. If `Vd` is not provided, integration is done in `V`. `J` is the grid-to-grid interpolation operator from `V` to `Vd`. If `J` is not provided, it is recomputed. If `Vd == V`, then `J` becomes `IdentityOperator(V)`.

ux,uy, ∇T are interpolated to a grid with higher polynomial order for dealiasing (over-integration) so we don't commit any "variational crimes"
