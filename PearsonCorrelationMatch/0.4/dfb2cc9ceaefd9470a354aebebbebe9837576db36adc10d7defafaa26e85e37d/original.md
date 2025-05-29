```
pearson_match(p::Real, d1, d2; n::Real=12, m::Real=128, kwargs...)
```

Compute the Pearson correlation coefficient to be used in a bivariate Gaussian copula.

# Fields

  * `p`: The target correltation between the marginal distributions.
  * `d1`: The first marginal distribution.
  * `d2`: The second marginal distribution.
  * `n`: The degree of the polynomial used to estimate the matching correlation.
  * `m`: The number of points used in the hermite polynomial interpolation.
  * `kwargs`: Additional keyword arguments. Currently unused.

# Examples

```julia-repl
julia> using Distributions

julia> d1 = Beta(2, 3); d2 = Binomial(20, 0.2);

julia> pearson_match(0.6, d1, d2)
0.6127531346934495
```
