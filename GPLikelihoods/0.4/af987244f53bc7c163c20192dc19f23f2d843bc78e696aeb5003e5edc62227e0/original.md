```
expected_loglikelihood(
    quadrature,
    lik,
    q_f::AbstractVector{<:Normal},
    y::AbstractVector,
)
```

This function computes the expected log likelihood:

$$
    ∫ q(f) log p(y | f) df
$$

where `p(y | f)` is the process likelihood. This is described by `lik`, which should be a callable that takes `f` as input and returns a Distribution over `y` that supports `loglikelihood(lik(f), y)`.

`q(f)` is an approximation to the latent function values `f` given by:

$$
    q(f) = ∫ p(f | u) q(u) du
$$

where `q(u)` is the variational distribution over inducing points. The marginal distributions of `q(f)` are given by `q_f`.

`quadrature` determines which method is used to calculate the expected log likelihood.

# Extended help

`q(f)` is assumed to be an `MvNormal` distribution and `p(y | f)` is assumed to have independent marginals such that only the marginals of `q(f)` are required.
