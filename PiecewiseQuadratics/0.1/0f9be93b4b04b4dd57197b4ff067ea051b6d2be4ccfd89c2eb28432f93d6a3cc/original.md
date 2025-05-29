```
scale(f::BoundedQuadratic, α::Real)
```

Return a new `BoundedQuadratic` that has been scaled by `α`. That is, given `f(x)` and `α`, returns `f(αx)`.

Note: this operation requires scaling the domain.

See also: [`scale!`](@ref)

# Example

```jldoctest
julia> bq = BoundedQuadratic(-1., 1., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-1.00000, 1.00000]

julia> scale(bq, 2.)
BoundedQuadratic: f(x) = 4.00000 x² + 2.00000 x + 1.00000, ∀x ∈ [-0.50000, 0.50000]

```
