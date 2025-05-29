```
fieldnames(T::Type [, ctx::Context])
```

`ctx`の下で[`AbstractStructFormat`](@ref)におけるパッキング/アンパッキング時に`T`のフィールド名を返します。

デフォルトは`Base.fieldnames(T)`です。
