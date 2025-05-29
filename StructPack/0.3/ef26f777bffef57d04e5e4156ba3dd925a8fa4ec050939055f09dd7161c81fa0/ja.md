```
fieldtypes(T::Type [, ctx::Context])
```

`ctx`の下で[`AbstractStructFormat`](@ref)におけるパッキング/アンパッキング時の`T`のフィールドタイプを返します。

デフォルトは`Base.fieldtypes(T)`です。
