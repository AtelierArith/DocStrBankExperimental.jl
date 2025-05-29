```
reverse(f::BoundedQuadratic)
```

Return `f` reversed over the `y` axis. That is, given `f(x)`, return `f(-x)`.

See also: [`reverse!`](@ref)

# Example

```jldoctest
julia> bq = BoundedQuadratic(-1., 2., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-1.00000, 2.00000]

julia> reverse(bq)
BoundedQuadratic: f(x) = 1.00000 x² - 1.00000 x + 1.00000, ∀x ∈ [-2.00000, 1.00000]

```
