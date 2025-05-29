```
maxdegree_complex(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}})
```

Return the maximal total complex degree of the monomials of `p`, i.e., `maximum(degree_complex, terms(p))`.

```
maxdegree_complex(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}}, v::AbstractVariable)
```

Return the maximal complex degree of the monomials of `p` in the variable `v`, i.e., `maximum(degree_complex.(terms(p), v))`.
