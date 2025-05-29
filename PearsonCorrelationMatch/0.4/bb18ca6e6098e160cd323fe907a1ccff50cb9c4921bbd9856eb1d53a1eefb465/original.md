```
pearson_match(R::AbstractMatrix{<:Real}, margins; n::Real=12, m::Real=128, kwargs...)
```

Pairwise compute the Pearson correlation coefficient to be used in a bivariate Gaussian copula. Ensures that the resulting matrix is a valid correlation matrix.

# Fields

  * `R`: The target correltation matrix of the marginal distributions.
  * `margins`: A list of marginal distributions.
  * `n`: The degree of the polynomial used to estimate the matching correlation.
  * `m`: The number of points used in the hermite polynomial interpolation.
  * `kwargs`: Additional keyword arguments. Currently unused.

# Examples

```julia-repl
julia> using Distributions

julia> margins = [Beta(2, 3), Uniform(0, 1), Binomial(20, 0.2)];

julia> rho = [
    1.0 0.3 0.6
    0.3 1.0 0.4
    0.6 0.4 1.0
];

julia> pearson_match(rho, margins)
3×3 Matrix{Float64}:
 1.0       0.309111  0.612753
 0.309111  1.0       0.418761
 0.612753  0.418761  1.0
```
