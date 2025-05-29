```
QuadratureTraining(; quadrature_alg = CubatureJLh(), reltol = 1e-6, abstol = 1e-3,
                    maxiters = 1_000, batch = 100)
```

A training strategy which treats the loss function as the integral of ||condition|| over the domain. Uses an Integrals.jl algorithm for computing the (adaptive) quadrature of this loss with respect to the chosen tolerances, with a batching `batch` corresponding to the maximum number of points to evaluate in a given integrand call.

## Keyword Arguments

  * `quadrature_alg`: quadrature algorithm,
  * `reltol`: relative tolerance,
  * `abstol`: absolute tolerance,
  * `maxiters`: the maximum number of iterations in quadrature algorithm,
  * `batch`: the preferred number of points to batch.

For more information on the argument values and algorithm choices, see [Integrals.jl](https://docs.sciml.ai/Integrals/stable/).
