```
shift(f::PiecewiseQuadratic, δ::Real)
```

Return `f` shifted along the `x`-axis by `δ`.

Note: for `δ > 0`, this is a right shift. For `δ < 0`, this is a left shift.

See also: [`shift!`](@ref)

# Example

```jldoctest
julia> f = PiecewiseQuadratic([BoundedQuadratic(-1., 0., 0., -5., 0.),
                               BoundedQuadratic(0., 2., 0., 2., 0.)])
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 5.00000 x , ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = + 2.00000 x , ∀x ∈ [0.00000, 2.00000]

julia> shift(f, 5.)
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 5.00000 x + 25.00000, ∀x ∈ [4.00000, 5.00000]
BoundedQuadratic: f(x) = + 2.00000 x - 10.00000, ∀x ∈ [5.00000, 7.00000]

```
