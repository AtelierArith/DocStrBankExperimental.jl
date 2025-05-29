```
set_exponent_vector!(a::MPoly{T}, i::Int, exps::Vector{Int}) where T <: RingElement
```

i 番目の指数ベクトルを提供されたベクトルに設定します。エントリは、環が作成されたときに提供された順序で変数の指数に対応します。修正された多項式が返されます。
