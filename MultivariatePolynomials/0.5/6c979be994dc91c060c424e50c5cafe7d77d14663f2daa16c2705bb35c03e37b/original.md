```
extdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}})
```

Returns the extremal total complex degrees of the monomials of `p`, i.e., `(mindegree_complex(p), maxdegree_complex(p))`.

```
extdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}}, v::AbstractVariable)
```

Returns the extremal complex degrees of the monomials of `p` in the variable `v`, i.e., `(mindegree_complex(p, v), maxdegree_complex(p, v))`.
