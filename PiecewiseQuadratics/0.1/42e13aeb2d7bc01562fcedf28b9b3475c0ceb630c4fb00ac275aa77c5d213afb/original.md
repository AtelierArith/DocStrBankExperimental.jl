```
get_tangent(f::BoundedQuadratic, x::Real)
```

Construct a new unbounded `BoundedQuadratic` representing the (unbounded) tangent line to `f` at the point `x`.

# Example

```jldoctest
julia> bq = BoundedQuadratic(-1., 1., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-1.00000, 1.00000]

julia> tangent = get_tangent(bq, 0.5)
BoundedQuadratic: f(x) = + 2.00000 x + 0.75000, ∀x ∈ ℝ

```
