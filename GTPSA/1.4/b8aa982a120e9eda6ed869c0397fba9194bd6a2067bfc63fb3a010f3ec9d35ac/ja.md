```
numtype(t::Number)
numtype(::Type{T}) where {T<:Number}
```

`TPS` の場合、`TPS` が表す数の型を返します。それ以外の場合は、その数の型を返します。
