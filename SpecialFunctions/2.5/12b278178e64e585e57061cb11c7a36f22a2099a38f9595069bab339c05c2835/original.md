```
loggamma(x)
```

Computes the logarithm of [`gamma`](@ref) for given `x`. If `x` is a `Real`, then it throws a `DomainError` if `gamma(x)` is negative.

If `x` is complex, then `exp(loggamma(x))` matches `gamma(x)` (up to floating-point error), but `loggamma(x)` may differ from `log(gamma(x))` by an integer multiple of $2πi$ (i.e. it may employ a different branch cut).

See also [`logabsgamma`](@ref) for real `x`.
