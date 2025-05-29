```
indicator(dom::Interval)
indicator(lb::Real, ub::Real)
```

Construct a PiecewiseQuadratic that is `0` on the interval and `Inf` everywhere else.

# Example

```jldoctest
julia> indicator(-5, 5)
Piecewise quadratic function:
BoundedQuadratic: f(x) = 0, ∀x ∈ [-5.00000, 5.00000]

```
