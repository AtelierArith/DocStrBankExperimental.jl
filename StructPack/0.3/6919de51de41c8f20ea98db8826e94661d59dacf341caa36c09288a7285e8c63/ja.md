```
keyformat(T::Type, state, fmt::Format [, ctx::Context])::Format
```

状態 `state` のイテレーションで、フォーマット `fmt` で `T` のエントリを保存する際のキーのフォーマットを返します。

このメソッドは、[`AbstractMapFormat`](@ref) で値をパックまたはアンパックする際に呼び出されます。
