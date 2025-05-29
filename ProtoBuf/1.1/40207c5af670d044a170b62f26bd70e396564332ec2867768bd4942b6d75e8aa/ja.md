```
encode(d::AbstractProtoDecoder, x::T) where {T}
```

型 `T` の構造体 `x` を `AbstractProtoEncoder` にラップされた `IO` に protobuf メッセージとしてエンコードします。

一般的な構造体については、これらのメソッドは [`protojl`](@ref) 関数を使用して生成されるべきです。
