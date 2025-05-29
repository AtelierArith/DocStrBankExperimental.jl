```
extend_dom(f::BoundedQuadratic)
```

Return an unbounded version of `f`.

See also: [`extend_dom!`](@ref)

# Example

```jldoctest
julia> bq = BoundedQuadratic(-1., 1., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-1.00000, 1.00000]

julia> extend_dom(bq)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ ℝ

```
