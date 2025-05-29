```
Derivative(sp::Space, k::AbstractVector{Int})
```

Return a partial derivative operator on a multivariate space. For example,

```julia
Dx = Derivative(Chebyshev()^2,[1,0]) # ∂/∂x
Dy = Derivative(Chebyshev()^2,[0,1]) # ∂/∂y
```

!!! tip
    Using a static vector as the second argument would help with type-stability.


# Examples

```jldoctest
julia> ∂y = Derivative(Chebyshev()^2, [0,1]);

julia> ∂y * Fun((x,y)->x^2 + y^2) ≈ Fun((x,y)->2y)
true
```
