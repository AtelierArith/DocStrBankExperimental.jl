```
elbo(
    sva::SparseVariationalApproximation,
    lfx::LatentFiniteGP,
    y::AbstractVector;
    num_data=length(y),
    quadrature=GPLikelihoods.DefaultExpectationMethod(),
)
```

潜在GPのELBOを、非共役の可能性がある尤度で計算します。
