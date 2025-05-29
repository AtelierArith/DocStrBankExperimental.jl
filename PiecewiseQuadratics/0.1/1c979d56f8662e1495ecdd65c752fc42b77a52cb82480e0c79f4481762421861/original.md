```
derivative(f::BoundedQuadratic, x::Real)
```

Evaluate the derivative of `f` at `x`, `f'(x)`.

# Example

```jldoctest
julia> bq = BoundedQuadratic(3., 2., 1.)
BoundedQuadratic: f(x) = 3.00000 x² + 2.00000 x + 1.00000, ∀x ∈ ℝ

julia> derivative(bq, 2.)
14.0

```
