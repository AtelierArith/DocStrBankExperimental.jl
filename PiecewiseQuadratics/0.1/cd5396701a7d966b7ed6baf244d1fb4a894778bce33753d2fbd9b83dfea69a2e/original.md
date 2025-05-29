```
get_line(x1::Real, y1::Real, x2::Real, y2::Real)
```

Construct a new unbounded `BoundedQuadratic` representing a line passing through `(x1, y1)` and `(x2, y2)`.

# Example

```jldoctest
julia> line = get_line(1., 2., 3., 4.)
BoundedQuadratic: f(x) = + 1.00000 x + 1.00000, ∀x ∈ ℝ

```
