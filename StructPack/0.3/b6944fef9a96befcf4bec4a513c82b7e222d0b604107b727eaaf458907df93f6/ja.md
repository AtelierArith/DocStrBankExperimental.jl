```
unpack(bytes::Vector{UInt8}, T::Type [, ctx::Context])::T
unpack(bytes::Vector{UInt8}, T::Type [, fmt::Format, ctx:::Context])::T
unpack(io::IO, T::Type, args...)::T
```

型 `T` の値のバイナリ msgpack 表現を、バイトベクター `bytes` またはストリーム `io` からフォーマット `fmt` でアンパックします。返される値は型 `T` であることが保証されています。

フォーマットが提供されていない場合、`format(T, ctx)` を介して `T` から導出されます。コンテキスト `ctx` はデフォルトで [`context`](@ref) です。
