```
indicator(dom::Interval)
indicator(lb::Real, ub::Real)
```

区間上で `0` であり、それ以外の場所では `Inf` である PiecewiseQuadratic を構築します。

# 例

```jldoctest
julia> indicator(-5, 5)
Piecewise quadratic function:
BoundedQuadratic: f(x) = 0, ∀x ∈ [-5.00000, 5.00000]

```
