```
midcov(X, [Y]; c=9)
```

Computes biweight midcovariance between the two vectors. If only one vector is provided the biweight midvariance will be calculated.

$$
\hat{\sigma}_{xy} = \frac{\sum_{u_i^2 \le 1,v_i^2 \le 1}{(x_i - \bar{x})(1 - u_i^2)^2(y_i - \bar{y})(1 - v_i^2)^2}}{\sum_{u_i^2 \le 1}{(1 - u_i^2)(1 - 5u_i^2)}\sum_{v_i^2 \le 1}{(1 - v_i^2)(1 - 5v_i^2)}}
$$

!!! warning
    `NaN` and `Inf` cannot be removed in the covariance calculation, so if they are present the returned value will be `NaN`. To prevent this, consider imputing values for the non-finite data.


# Examples

```jldoctest
julia> X = 10 .* randn(rng, 1000, 2) .+ 50;


julia> midcov(X[:, 1], X[:, 2])
-1.058463590812247

julia> midcov(X[:, 1]) ≈ midvar(X[:, 1])
true

julia> X[3, 2] = NaN;


julia> midcov(X[:, 1], X[:, 2])
NaN
```

# References

1. [NIST: biweight midcovariance](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/biwmidc.htm)

# See Also

[`scale`](@ref), [`midvar`](@ref), [`midcor`](@ref)
