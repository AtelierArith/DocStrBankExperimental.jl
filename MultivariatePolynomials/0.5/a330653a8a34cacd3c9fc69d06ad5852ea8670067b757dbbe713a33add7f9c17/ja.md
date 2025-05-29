```
term_type(p::AbstractPolynomialLike)
```

`p`の項の型を返します。

```
term_type(::Type{PT}) where PT<:AbstractPolynomialLike
```

型`PT`の多項式の項の型を返します。

```
term_type(p::AbstractPolynomialLike, ::Type{T}) where T
```

`p`の項の型を返しますが、係数の型は`T`です。

```
term_type(::Type{PT}, ::Type{T}) where {PT<:AbstractPolynomialLike, T}
```

型`PT`の多項式の項の型を返しますが、係数の型は`T`です。
