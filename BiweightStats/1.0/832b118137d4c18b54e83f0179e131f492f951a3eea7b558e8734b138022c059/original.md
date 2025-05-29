```
midcov(X::AbstractMatrix; dims=1, c=9)
```

Computes the variance-covariance matrix using the biweight midcovariance. By default, each column is a separate variable, so an `(M, N)` matrix with `dims=1` will create an `(N, N)` covariance matrix. If `dims=2`, though, each row will become a variable, leading to an `(M, M)` covariance matrix.

!!! warning
    `NaN` and `Inf` cannot be removed in the covariance calculation, so if they are present the returned value will be `NaN`. To prevent this, consider imputing values for the non-finite data.


# Examples

```jldoctest
julia> X = 10 .* randn(rng, 1000, 3) .+ 50;


julia> C = midcov(X)
3×3 Matrix{Float64}:
 100.918    -1.05846    -2.88515
  -1.05846  94.702      -0.490742
  -2.88515  -0.490742  100.699

julia> size(midcov(X; dims=2))
(1000, 1000)
```

# References

1. [NIST: biweight midcovariance](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/biwmidc.htm)

# See Also

[`scale`](@ref), [`midvar`](@ref), [`midcor`](@ref)
