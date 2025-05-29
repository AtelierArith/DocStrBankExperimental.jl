```
valueformat(T::Type, state, fmt::Format [, ctx::Context])::Format
```

状態 `state` の反復時に、フォーマット `fmt` で `T` のエントリを保存する際の値のフォーマットを返します。

このメソッドは、[`AbstractVectorFormat`](@ref) および [`AbstractMapFormat`](@ref) で値をパックまたはアンパックする際に使用されます。
