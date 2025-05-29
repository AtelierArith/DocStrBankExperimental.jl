```
constant(f::AbstractFunction[, ::Type{T}]) where {T}
```

スカラー値関数の定数項、またはベクトル値関数の定数ベクトルを返します。

`f` が型指定されておらず、`T` が提供されている場合、`zero(T)` を返します。
