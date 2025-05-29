```
domain(f::BoundedQuadratic)
```

Return the Interval on which the BoundedQuadratic is defined.

# Example

```jldoctest
julia> bq = BoundedQuadratic(0., 5., 3., 2., 1.)
BoundedQuadratic: f(x) = 3.00000 x² + 2.00000 x + 1.00000, ∀x ∈ [0.00000, 5.00000]

julia> dom = domain(bq)
[0.00000, 5.00000]

```
