現在のコンテキストをオーバーライドする特別なフォーマット。

特に、次のようにパッキング（または同様にアンパッキング）することができます。

```
pack(val, ContextFormat{C, F}(), C2())
```

これは次のように等価です。

```
pack(val, F(), C())
```

ここで、元のコンテキスト `C2 <: Context` は無視されます。

このフォーマットは、例えば、[`fieldformats`](@ref) と組み合わせて使用するのに便利で、構造体の異なるフィールドが異なるコンテキストでパッキング / アンパッキングできることを強制します。
