```
interpolate(vals::Vector{T})::SimplePolynomial where {T<:Number}
```

数値のリスト `vals` が与えられたとき、そのリストを生成する多項式 `p` を見つけます。つまり、`p(0)` はリストの最初の値を、`p(1)` は2番目の値を、というように続きます。
