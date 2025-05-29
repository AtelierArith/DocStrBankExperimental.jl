```
envelope(f::PiecewiseQuadratic)
```

Computes the greatest convex lower bound of a `PiecewiseQuadratic` `f`.

# Example

```jldoctest
julia> f = PiecewiseQuadratic([BoundedQuadratic(-Inf, 0., 0., 1., 0.),
                               BoundedQuadratic(0., 3., 0., 0., 0.)])
Piecewise quadratic function:
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [-Inf, 0.00000]
BoundedQuadratic: f(x) = 0, ∀x ∈ [0.00000, 3.00000]

julia> envelope(f)
Piecewise quadratic function:
BoundedQuadratic: f(x) = + 1.00000 x - 3.00000, ∀x ∈ [-Inf, 3.00000]

```
