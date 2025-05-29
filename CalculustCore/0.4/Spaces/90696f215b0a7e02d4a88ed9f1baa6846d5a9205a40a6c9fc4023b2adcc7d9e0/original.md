```
laplaceOp(V::AbstractSpace, discr::AbstractDiscretization)
```

Laplace Operator: -Δ

Returns the negative Laplace operator over `V` per discretization scheme `discr`. As the Laplace operator (laplacian) is a negative-definitie operator, we return the negative laplacian which is a positive-definite operator.
