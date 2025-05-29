```
basis(p::P, i::Int)
basis(::Type{<:AbstractPolynomial}, i::Int, var=:x)
```

与えられた多項式型のi番目の基底要素を返し、オプションで指定された変数を使用します。
