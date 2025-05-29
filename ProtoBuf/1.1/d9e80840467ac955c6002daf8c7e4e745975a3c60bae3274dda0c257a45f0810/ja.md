```
decode(d::AbstractProtoDecoder, ::Type{T}) where {T}
```

`AbstractProtoDecoder`でラップされた`IO`からプロトコルバッファメッセージをデコードし、型Tの構造体に変換します。

一般的な構造体については、これらのメソッドは[`protojl`](@ref)関数を使用して生成する必要があります。
