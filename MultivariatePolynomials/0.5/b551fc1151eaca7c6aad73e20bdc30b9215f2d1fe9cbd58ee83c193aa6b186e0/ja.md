```
constant_monomial(p::AbstractPolynomialLike)
```

`p`と同じ変数を持つ`p`の単項式の単項式型の定数単項式を返します。

```
constant_monomial(::Type{PT}) where {PT<:AbstractPolynomialLike}
```

型`PT`の多項式の単項式型の定数単項式を返します。
