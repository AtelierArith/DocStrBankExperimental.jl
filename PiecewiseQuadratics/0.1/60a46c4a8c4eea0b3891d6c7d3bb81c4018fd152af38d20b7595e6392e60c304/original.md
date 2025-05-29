```
is_point(f::BoundedQuadratic)
```

Return `true` if the BoundedQuadratic is defined only on a single point (`lb == ub`).

See also: [`is_almost_point`](@ref)

# Example

```jldoctest
julia> bq = BoundedQuadratic(0., 5., 3., 2., 1.)
BoundedQuadratic: f(x) = 3.00000 x² + 2.00000 x + 1.00000, ∀x ∈ [0.00000, 5.00000]

julia> is_point(bq)
false

julia> bq = BoundedQuadratic(5., 5., 3., 2., 1.)
BoundedQuadratic: f(x) = 3.00000 x² + 2.00000 x + 1.00000, ∀x ∈ [5.00000, 5.00000]

julia> is_point(bq)
true

```
