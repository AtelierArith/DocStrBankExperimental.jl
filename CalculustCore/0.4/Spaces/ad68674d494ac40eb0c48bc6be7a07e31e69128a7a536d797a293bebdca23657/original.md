```julia
diffusionOp(ν, V, discr; ν_update_func)

```

Diffusion operator: -∇⋅(ν∇⋅)

Returns the diffusion operator where `ν` is the space-varying diffusion coefficient in `V`. `ν` can be updated per `ν_update_func` which expets the same signature as `SciMLOperators.DiagonalOperator`.

It is assumed that `ν` is a function in space `V`. However, if `V` is a transformed space, then `ν` is a function in the physical space, i.e. `transform(V)`.
