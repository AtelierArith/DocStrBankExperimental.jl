```
construct(T::Type, val, fmt::Format [, ctx::Context])::T
```

値 `val` を `fmt` に従ってアンパックし、型 `T` のオブジェクトを返します。`val` の型は、アンパックに使用されたフォーマット `fmt` に依存します。

デフォルトでは `T(val)` ですが、`T`、`fmt`、および `ctx` の任意の組み合わせに対して上書きすることができます。
