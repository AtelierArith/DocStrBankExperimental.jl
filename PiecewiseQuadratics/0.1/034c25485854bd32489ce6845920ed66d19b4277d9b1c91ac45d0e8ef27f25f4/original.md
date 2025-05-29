```
 simplify(f::PiecewiseQuadratic)
```

Return a simplified piecewise quadratic `f`.

A BoundedQuadratic `f_i` and and the current rightmost piece should be combined (to become the new rightmost piece) if

  * Either of `f_i` or the rightmost piece is a point and they overlap at their lower and upper endpoints respectively
  * `f_i` and the rightmost piece have the same coefficients and they correspond at their lower and upper endpoints respectively (they're just currently separate parts of the same function).

We also eliminate functions that are points at Inf or -Inf if they come up.

# Example

```jldoctest
julia> f = PiecewiseQuadratic([BoundedQuadratic(-1., 0., 0., -1., 0.),
                                      BoundedQuadratic(0., 0., 0., 0., 0.),
                                      BoundedQuadratic(0., 1., 0., 1., 0.),
                                      BoundedQuadratic(1., 2., 0., 1., 0.),
                                      BoundedQuadratic(3., 5., 1., 1., 1.)])
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 1.00000 x , ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = 0, ∀x ∈ [0.00000, 0.00000]
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [0.00000, 1.00000]
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [1.00000, 2.00000]
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [3.00000, 5.00000]

julia> simplify(f)
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 1.00000 x , ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [0.00000, 2.00000]
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [3.00000, 5.00000]

```
