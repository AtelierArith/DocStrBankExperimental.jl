```
midvar(X; c=9, M=nothing)
midvar(X::AbstractArray; dims=:, kwargs...)
```

Compute the biweight midvariance of the variable.

$$
\hat{\sigma}^2 = \frac{n\sum^n_{u_i^2 \le 1}{(y_i - \bar{y})^2(1 - u_i^2)^4}}{\left[\sum_{u_i^2 \le 1}{(1 - u_i^2)(1 - 5u_i^2)}\right]^2}
$$

# Examples

```jldoctest
julia> X = 10 .* randn(rng, 1000) .+ 50;


julia> midvar(X)
100.9183702382928
```

# References

1. [NIST: biweight midvariance](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/biwmidv.htm)

# See Also

[`scale`](@ref), [`midcor`](@ref), [`midcov`](@ref)
