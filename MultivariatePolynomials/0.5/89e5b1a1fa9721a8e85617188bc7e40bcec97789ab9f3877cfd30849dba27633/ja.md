```
polynomial_type(p::AbstractPolynomialLike)
```

`p`が多項式に変換された場合の型を返します。

```
polynomial_type(::Type{PT}) where PT<:AbstractPolynomialLike
```

`polynomial_type(::PT)`と同じものを返します。

```
polynomial_type(p::AbstractPolynomialLike, ::Type{T}) where T
```

`p`が係数型`T`の多項式に変換された場合の型を返します。

```
polynomial_type(::Type{PT}, ::Type{T}) where {PT<:AbstractPolynomialLike, T}
```

`polynomial_type(::PT, ::Type{T})`と同じものを返します。
