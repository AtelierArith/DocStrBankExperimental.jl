```
extdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}})
```

`p`の単項式の極値の総複素次数を返します。すなわち、`(mindegree_complex(p), maxdegree_complex(p))`です。

```
extdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}}, v::AbstractVariable)
```

変数`v`における`p`の単項式の極値の複素次数を返します。すなわち、`(mindegree_complex(p, v), maxdegree_complex(p, v))`です。
