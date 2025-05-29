```
tilt(f::BoundedQuadratic, α::Real)
```

Return `f` tilted by `α`. This shifts linear coefficient `q` by `α`.

See also: [`tilt!`](@ref)

# Example

```jldoctest
julia> bq = BoundedQuadratic(-1., 1., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-1.00000, 1.00000]

julia> tilt(bq, 2.)
BoundedQuadratic: f(x) = 1.00000 x² + 3.00000 x + 1.00000, ∀x ∈ [-1.00000, 1.00000]

```
