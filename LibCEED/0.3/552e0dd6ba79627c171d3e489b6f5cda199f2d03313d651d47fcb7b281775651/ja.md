```
axpy!(a::Real, x::CeedVector, y::CeedVector)
```

`y`を`x*a + y`で上書きします。ここで、`a`はスカラーです。`y`を返します。

!!! warning "引数の順序が異なる"
    `LinearAlgebra.axpy!`と一貫性を持たせるために、引数は次の順序で渡されます：`a`、`x`、`y`。これはC関数`CeedVectorAXPY`の引数の順序とは異なります。

