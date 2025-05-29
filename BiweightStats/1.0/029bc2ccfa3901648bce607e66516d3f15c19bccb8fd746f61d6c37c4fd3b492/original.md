```
midcor(X::AbstractMatrix; dims=1, c=9)
```

Computes the correlation matrix using the biweight midcorrealtion. By default, each column of the matrix is a separate variable, so an `(M, N)` matrix with `dims=1` will create an `(N, N)` correlation matrix. If `dims=2`, though, each row will become a variable, leading to an `(M, M)` correlation matrix. The diagonal will always be one.

# Examples

```jldoctest
julia> X = 10 .* randn(rng, 1000, 3) .+ 50;


julia> C = midcor(X)
3×3 Matrix{Float64}:
  1.0        -0.0108271  -0.0286201
 -0.0108271   1.0        -0.0050253
 -0.0286201  -0.0050253   1.0

julia> size(midcor(X; dims=2))
(1000, 1000)
```

# References

1. [Wikipedia](https://en.wikipedia.org/wiki/Biweight_midcorrelation)
2. [NIST: Biweight midcorrelation](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/biwmidcr.htm)

# See Also

[`midvar`](@ref), [`midcov`](@ref), [`scale`](@ref)
