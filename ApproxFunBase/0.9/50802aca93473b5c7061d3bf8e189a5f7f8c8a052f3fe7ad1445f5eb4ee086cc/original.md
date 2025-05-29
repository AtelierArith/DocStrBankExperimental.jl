```
ProductFun(coeffs::AbstractMatrix{T}, sp::AbstractProductSpace; [tol=100eps(T)], [chopping=false]) where {T<:Number}
```

Represent a bivariate function `f` in terms of the coefficient matrix `coeffs`, where the coefficients are obtained using a bivariate transform of the function `f` in the basis `sp`.

# Examples

```jldoctest
julia> P = ProductFun([0 0; 0 1], Chebyshev() ⊗ Chebyshev()) # corresponds to (x,y) -> x*y
ProductFun on Chebyshev() ⊗ Chebyshev()

julia> P(0.1, 0.2) ≈ 0.1 * 0.2
true
```
