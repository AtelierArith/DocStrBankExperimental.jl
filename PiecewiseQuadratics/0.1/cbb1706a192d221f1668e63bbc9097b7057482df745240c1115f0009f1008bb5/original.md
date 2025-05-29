```
perspective(f::PiecewiseQuadratic, α::Real)
```

Return the perspective function of `f`. That is, given `f(x)` and `α`, return `α * f(x / α)`.

Note: that this operation requires scaling of the domain.

See also: [`perspective!`](@ref)

# Example

```jldoctest
julia> f = PiecewiseQuadratic([BoundedQuadratic(-1., 0., 0., -5., 0.),
                               BoundedQuadratic(0., 2., 0., 2., 0.)])
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 5.00000 x , ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = + 2.00000 x , ∀x ∈ [0.00000, 2.00000]

julia> persp = perspective(f, 5.)
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 5.00000 x , ∀x ∈ [-5.00000, 0.00000]
BoundedQuadratic: f(x) = + 2.00000 x , ∀x ∈ [0.00000, 10.00000]

```
