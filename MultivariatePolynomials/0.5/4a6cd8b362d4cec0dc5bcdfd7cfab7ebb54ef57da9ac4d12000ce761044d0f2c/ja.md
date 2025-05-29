```
mindegree_complex(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}})
```

`p`の単項式の最小総複素次数を返します。すなわち、`minimum(degree_complex, terms(p))`です。

```
mindegree_complex(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}}, v::AbstractVariable)
```

変数`v`における`p`の単項式の最小複素次数を返します。すなわち、`minimum(degree_complex.(terms(p), v))`です。
