```
perspective(f::BoundedQuadratic, α::Real)
```

Return the perspective function of `f`. That is, given `f(x)` and `α`, return `α * f(x / α)`.

Note: that this operation requires scaling of the domain.

See also: [`perspective!`](@ref)

# Example

```jldoctest
julia> bq = BoundedQuadratic(-1., 1., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-1.00000, 1.00000]

julia> perspective(bq, 2.)
BoundedQuadratic: f(x) = 0.50000 x² + 1.00000 x + 2.00000, ∀x ∈ [-2.00000, 2.00000]

```
