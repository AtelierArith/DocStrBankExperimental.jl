```
Derivative(k)
```

Return the `k`-th derivative, acting on an unset space. Spaces will be inferred when applying or manipulating the operator. If `k` is an `Int`, this returns a derivative in an univariate space. If `k` is an `AbstractVector{Int}`, this returns a partial derivative in a multivariate space.

# Examples

```jldoctest
julia> Derivative(1) * Fun(x->x^2) ≈ Fun(x->2x)
true

julia> Derivative([0,1]) * Fun((x,y)->x^2+y^2) ≈ Fun((x,y)->2y)
true
```
