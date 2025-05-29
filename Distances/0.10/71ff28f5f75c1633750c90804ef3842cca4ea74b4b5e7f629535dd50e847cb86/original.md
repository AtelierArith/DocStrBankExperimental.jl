```
Euclidean([thresh])
```

Create a euclidean metric.

When computing distances among large numbers of points, it can be much more efficient to exploit the formula

```
(x-y)^2 = x^2 - 2xy + y^2
```

However, this can introduce roundoff error. `thresh` (which defaults to 0) specifies the relative square-distance tolerance on `2xy` compared to `x^2 + y^2` to force recalculation of the distance using the more precise direct (elementwise-subtraction) formula.

# Example:

```julia
julia> x = reshape([0.1, 0.3, -0.1], 3, 1);

julia> pairwise(Euclidean(), x, x)
1×1 Array{Float64,2}:
 7.45058e-9

julia> pairwise(Euclidean(1e-12), x, x)
1×1 Array{Float64,2}:
 0.0
```
