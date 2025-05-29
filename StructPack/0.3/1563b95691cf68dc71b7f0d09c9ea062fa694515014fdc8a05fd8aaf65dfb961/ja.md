```
typeparamformats(T::Type [, ctx::Context])
```

`ctx`の下でパッキング/アンパッキングする際に、`T`の型パラメータのフォーマットを返します。

各型パラメータのデフォルトは`DefaultFormat()`です。

このメソッドは、[`TypeFormat`](@ref)および[`TypedFormat`](@ref)を介して型をパッキング/アンパッキングする際に参照されます。
