```
mindegree_complex(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}})
```

Return the minimal total complex degree of the monomials of `p`, i.e., `minimum(degree_complex, terms(p))`.

```
mindegree_complex(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}}, v::AbstractVariable)
```

Return the minimal complex degree of the monomials of `p` in the variable `v`, i.e., `minimum(degree_complex.(terms(p), v))`.
