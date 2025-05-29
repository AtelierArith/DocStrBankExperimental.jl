```
scale(f::PiecewiseQuadratic, α::Real)
```

Return a new `PiecewiseQuadratic` that has been scaled by `α`. That is, given `f(x)` and `α`, returns `f(αx)`.

Note: this operation requires scaling the domain.

See also: [`scale!`](@ref)

# Example

```jldoctest
julia> f = PiecewiseQuadratic([BoundedQuadratic(-1., 0., 0., -1., 0.),
                               BoundedQuadratic(0., 1., 0., 1., 0.),
                               BoundedQuadratic(1., 5., 1., 1., 1.)])
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 1.00000 x , ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [0.00000, 1.00000]
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [1.00000, 5.00000]

julia> scale(f, 5)
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 5.00000 x , ∀x ∈ [-0.20000, 0.00000]
BoundedQuadratic: f(x) = + 5.00000 x , ∀x ∈ [0.00000, 0.20000]
BoundedQuadratic: f(x) = 25.00000 x² + 5.00000 x + 1.00000, ∀x ∈ [0.20000, 1.00000]

```
