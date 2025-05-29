```
pearson_bounds(margins; n::Real=12, m::Real=128, kwargs...)
```

Determine the range of admissible Pearson correlations pairwise between a list of distributions.

# Fields

  * `margins`: A list of marginal distributions.
  * `n`: The degree of the polynomial used to estimate the bounds.
  * `m`: The number of points used in the hermite polynomial interpolation.
  * `kwargs`: Additional keyword arguments. Currently unused.

# Examples

```julia-repl
julia> using Distributions

julia> margins = [Exponential(3.14), NegativeBinomial(20, 0.2), LogNormal(2.718)];

julia> lower, upper = pearson_bounds(margins);

julia> lower
3×3 Matrix{Float64}:
  1.0       -0.855395  -0.488737
 -0.855395   1.0       -0.704403
 -0.488737  -0.704403   1.0

julia> upper
3×3 Matrix{Float64}:
 1.0       0.941367  0.939671
 0.941367  1.0       0.815171
 0.939671  0.815171  1.0
```
