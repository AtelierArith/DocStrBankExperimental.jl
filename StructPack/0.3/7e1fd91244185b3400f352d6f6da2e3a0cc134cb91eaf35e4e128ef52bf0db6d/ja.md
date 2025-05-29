```
keytype(T::Type, state, fmt::Format [, ctx::Context])::Type
```

`fmt` 形式で `T` のエントリを保存する際のイテレーション状態 `state` におけるキーの型を返します。

このメソッドは [`AbstractMapFormat`](@ref) で値をアンパックする際に呼び出されます。
