```
(f::BoundedQuadratic)(x::Real)
```

Evaluate `f(x)` if `x` is in the domain of `f`, else return `Inf`.

# Example

```jldoctest
julia> bq = BoundedQuadratic(3., 2., 1.)
BoundedQuadratic: f(x) = 3.00000 x² + 2.00000 x + 1.00000, ∀x ∈ ℝ

julia> bq(1.)
6.0

```
