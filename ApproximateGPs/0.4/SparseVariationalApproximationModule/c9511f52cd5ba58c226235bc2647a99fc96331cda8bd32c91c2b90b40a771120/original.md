```
elbo(
    sva::SparseVariationalApproximation,
    lfx::LatentFiniteGP,
    y::AbstractVector;
    num_data=length(y),
    quadrature=GPLikelihoods.DefaultExpectationMethod(),
)
```

Compute the ELBO for a LatentGP with a possibly non-conjugate likelihood.
