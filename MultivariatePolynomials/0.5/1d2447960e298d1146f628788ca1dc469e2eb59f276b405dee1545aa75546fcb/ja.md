```
maxhalfdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}})
```

`p`の単項式の最大半次数を返します。すなわち、`maximum(halfdegree, terms(p))`です。
