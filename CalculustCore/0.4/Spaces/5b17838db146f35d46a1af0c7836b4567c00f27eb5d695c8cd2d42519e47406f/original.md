```
diffusionOp(ν::Number, V::AbstractSpace, discr::AbstractDiscretization)
```

Diffusion operator: -νΔ

Returns the negative Laplace Operator scaled by diffusion coefficient `ν`. `ν` can be updated per `ν_update_func` which expects the same signature as `SciMLOperators.ScalarOperator`. All positional arguments besides `ν` are passed down to `laplaceOp` to form the negative lapalcian.
