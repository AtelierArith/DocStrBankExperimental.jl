```
scale(X; c=9, M=nothing)
scale(X::AbstractArray; dims=:, kwargs...)
```

Compute the biweight scale of the variable. This is the same as the square-root of the midvariance.

$$
\hat{\sigma} = \frac{\sqrt{n\sum^n_{u_i^2 \le 1}{(y_i - \bar{y})^2(1 - u_i^2)^4}}}{\sum^n_{u_i^2 \le 1}{(1 - u_i^2)(1 - 5u_i^2)}}
$$

# Examples

```jldoctest
julia> X = 10 .* randn(rng, 1000) .+ 50;


julia> scale(X)
10.045813567765071
```

# References

1. [NIST: biweight scale](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/biwscale.htm)

# See Also

[`midcor`](@ref), [`midvar`](@ref), [`midcov`](@ref)
