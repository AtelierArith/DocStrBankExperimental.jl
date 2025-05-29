```
minhalfdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}})
```

Return the minmal half degree of the monomials of `p`, i.e., `minimum(halfdegree, terms(p))`
