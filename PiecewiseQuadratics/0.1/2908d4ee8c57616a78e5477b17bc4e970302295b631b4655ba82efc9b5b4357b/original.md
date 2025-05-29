```
PiecewiseQuadratic()
PiecewiseQuadratic(f::BoundedQuadratic)
PiecewiseQuadratic(f_list::Vector{BoundedQuadratic}[; simplify_result=false])
```

Represents piecewise quadratic function, where each piece is a `BoundedQuadratic`.

The fields represent:

  * `f_list`: a `Vector` of `BoundedQuadratic` functions

# Example

```jldoctest
julia> left = BoundedQuadratic(-Inf, 0., 0., -1., 0.)
BoundedQuadratic: f(x) = - 1.00000 x , ∀x ∈ [-Inf, 0.00000]

julia> right = BoundedQuadratic(0., Inf, 0., 1., 0.)
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [0.00000, Inf]

julia> pwq = PiecewiseQuadratic([left, right])
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 1.00000 x , ∀x ∈ [-Inf, 0.00000]
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [0.00000, Inf]

```
