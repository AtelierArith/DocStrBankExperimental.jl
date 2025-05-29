```
pearson_bounds(d1, d2; n::Real=20, m::Real=128, kwargs...)
```

Determine the range of admissible Pearson correlations between two distributions.

# Fields

  * `d1`: The first marginal distribution.
  * `d2`: The second marginal distribution.
  * `n`: The degree of the polynomial used to estimate the bounds.
  * `m`: The number of points used in the hermite polynomial interpolation.
  * `kwargs`: Additional keyword arguments. Currently unused.

# Details

The accuracy of the bounds depends on the degree of the polynomial and the number of hermite points. Be careful not to set the polynomial degree too high as Runge's theorem states that a polynomial of too high degree would cause oscillation at the edges of the interval and reduce accuracy.

In general raising the number of hermite points will result in better accuracy, but comes with a small performance hit. Furthermore the number of hermite points should be higher than the degree of the polynomial.

# Examples

```julia-repl
julia> using Distributions

julia> d1 = Exponential(3.14); d2 = NegativeBinomial(20, 0.2);

julia> pearson_bounds(d1, d2)
(lower = -0.8553947509241561, upper = 0.9413665073003636)
```
