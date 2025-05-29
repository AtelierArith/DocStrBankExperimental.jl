```
Tuple(x::ProductSimplex{T}) where T -> T <: Tuple{Vararg{AbstractSimplex}}
components(x::ProductSimplex{T}) where T -> T <: Tuple{Vararg{AbstractSimplex}}
```

`x`の構成単体のタプルを返します。

!!! note
    関数`components`は非推奨です。代わりに`Tuple`を使用してください。

