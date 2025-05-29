```
expected_loglikelihood(::DefaultExpectationMethod, lik, q_f::AbstractVector{<:Normal}, y::AbstractVector)
```

The expected log likelihood, using the default quadrature method for the given likelihood. (The default quadrature method is defined by `default_expectation_method(lik)`, and should be the closed form solution if it exists, but otherwise defaults to Gauss-Hermite quadrature.)
