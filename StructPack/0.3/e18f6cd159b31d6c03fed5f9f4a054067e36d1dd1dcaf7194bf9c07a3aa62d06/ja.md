```
valuetype(T::Type, fmt::Format, state [, ctx::Context])::Type
```

フォーマット `fmt` で `T` のエントリを保存する際のイテレーション状態 `state` における値の型を返します。

このメソッドは、[`AbstractVectorFormat`](@ref) および [`AbstractMapFormat`](@ref) で値をアンパックする際に使用されます。
