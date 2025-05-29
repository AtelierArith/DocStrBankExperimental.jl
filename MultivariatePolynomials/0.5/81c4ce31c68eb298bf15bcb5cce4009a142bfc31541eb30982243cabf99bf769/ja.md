```
maxdegree_complex(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}})
```

`p`の単項式の最大の総複素次数を返します。すなわち、`maximum(degree_complex, terms(p))`です。

```
maxdegree_complex(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}}, v::AbstractVariable)
```

変数`v`における`p`の単項式の最大の複素次数を返します。すなわち、`maximum(degree_complex.(terms(p), v))`です。
