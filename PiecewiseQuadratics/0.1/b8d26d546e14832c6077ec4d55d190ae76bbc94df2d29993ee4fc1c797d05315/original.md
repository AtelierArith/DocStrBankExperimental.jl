```
is_convex(f::PiecewiseQuadratic)
```

Return `true` if `f` is convex.

A `PiecewiseQuadratic` is convex if for all `i`:

  * `f_i` is convex
  * `f_i.ub == f_{i+1}.lb`
  * `derivative(f_i)(f_i.ub) <= derivative(f_{i+1})(f_{i+1}.lb)`

# Example

```jldoctest
julia> left = BoundedQuadratic(-Inf, 0., 0., -1., 0.)
BoundedQuadratic: f(x) = - 1.00000 x , ∀x ∈ [-Inf, 0.00000]

julia> right = BoundedQuadratic(0., Inf, 0., 1., 0.)
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [0.00000, Inf]

julia> pwq = PiecewiseQuadratic([left, right])
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 1.00000 x , ∀x ∈ [-Inf, 0.00000]
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [0.00000, Inf]

julia> is_convex(pwq)
true

```
