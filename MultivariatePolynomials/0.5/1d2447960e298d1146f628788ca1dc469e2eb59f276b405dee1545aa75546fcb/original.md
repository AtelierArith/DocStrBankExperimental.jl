```
maxhalfdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}})
```

Return the maximal half degree of the monomials of `p`, i.e., `maximum(halfdegree, terms(p))`
