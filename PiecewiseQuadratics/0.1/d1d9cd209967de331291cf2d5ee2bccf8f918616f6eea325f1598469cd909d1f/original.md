```
restrict_dom(f::BoundedQuadratic, dom::Interval)
restrict_dom(f::BoundedQuadratic, lb::Real, ub::Real)
```

Return a new BoundedQuadratic with domain restricted to the intersect of the passed domain.

See also: [`restrict_dom!`](@ref)

# Example

```jldoctest
julia> bq = BoundedQuadratic(-10., 10., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-10.00000, 10.00000]

julia> restrict_dom(bq, 2., 3.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [2.00000, 3.00000]

```
