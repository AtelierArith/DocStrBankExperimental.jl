```
is_signed(::T)
is_signed(T::Type)
```

は、型 `T` の数値が同じ型を保持しながら符号を反転できるかどうかを返します。`false` は、`T <: Union{U,Rational{U},Complex{U}} where {U<:Union{Bool,Unsigned}}` およびこれらのベア数値型に基づく量に対して返されます。
