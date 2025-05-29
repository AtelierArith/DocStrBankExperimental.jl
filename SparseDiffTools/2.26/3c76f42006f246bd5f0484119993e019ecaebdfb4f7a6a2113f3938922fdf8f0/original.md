```
ApproximateJacobianSparsity(; ntrials = 5, rng = Random.default_rng(),
    epsilon = nothing, alg = GreedyD1Color())
```

Use `ntrials` random vectors to compute the sparsity pattern of the Jacobian. This is an approximate method and the sparsity pattern may not be exact.

## Keyword Arguments

```
- `ntrials`: The number of random vectors to use for computing the sparsity pattern
- `rng`: The random number generator used for generating the random vectors
- `alg`: The algorithm used for computing the matrix colors
- `epsilon`: For Finite Differencing based Jacobian Approximations, any number smaller
  than `epsilon` is considered to be zero. If `nothing` is specified, then this value
  is calculated as `100 * eps(eltype(x))`
```
