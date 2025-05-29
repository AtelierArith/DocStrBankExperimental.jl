```
gcp(X::Array, r;
    loss = GCPLosses.LeastSquares(),
    constraints = default_constraints(loss),
    algorithm = default_algorithm(X, r, loss, constraints),
    init = default_init(X, r, loss, constraints, algorithm))
```

Compute an approximate rank-`r` CP decomposition of the tensor `X` with respect to the loss function `loss` and return a `CPD` object.

Keyword arguments:

  * `constraints` : a `Tuple` of constraints on the factor matrices `U = (U[1],...,U[N])`.
  * `algorithm`   : algorithm to use

Conventional CP corresponds to the default `GCPLosses.LeastSquares()` loss with the default of no constraints (i.e., `constraints = ()`).

If the LossFunctions.jl package is also loaded, `loss` can also be a loss function from that package. Check `GCPDecompositions.LossFunctionsExt.SupportedLosses` to see what losses are supported.

See also: `CPD`, `GCPLosses`, `GCPConstraints`, `GCPAlgorithms`.
