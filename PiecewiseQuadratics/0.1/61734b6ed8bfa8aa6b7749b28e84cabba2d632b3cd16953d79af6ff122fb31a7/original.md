```
shift(f::BoundedQuadratic, δ::Real)
```

Return `f` shifted along the `x`-axis by `δ`.

Note: for `δ > 0`, this is a right shift. For `δ < 0`, this is a left shift.

See also: [`shift!`](@ref)

# Example

```jldoctest
julia> bq = BoundedQuadratic(-1., 1., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-1.00000, 1.00000]

julia> shift(bq, 2.)
BoundedQuadratic: f(x) = 1.00000 x² - 3.00000 x + 3.00000, ∀x ∈ [1.00000, 3.00000]

```
