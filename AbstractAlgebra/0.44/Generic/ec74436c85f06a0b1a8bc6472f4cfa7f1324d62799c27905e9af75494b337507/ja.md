```
exponent_vector(a::MPoly{T}, i::Int) where T <: RingElement
```

多項式の i 番目の項に対応する指数ベクトルを返します。項の番号は $1$ から始まり、指数はリングが作成されたときに供給された変数の順序で与えられます。
