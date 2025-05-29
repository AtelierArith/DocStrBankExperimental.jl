```
minhalfdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}})
```

`p`の単項式の最小半次数を返します。すなわち、`minimum(halfdegree, terms(p))`です。
