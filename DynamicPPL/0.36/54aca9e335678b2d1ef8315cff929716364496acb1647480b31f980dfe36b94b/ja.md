```
PrefixContext(vn::VarName[, context::AbstractContext])
PrefixContext(vn::Val{sym}[, context::AbstractContext]) where {sym}
```

ラップされた `context` を使用してモデルを実行するためのコンテキストを作成し、すべてのパラメータを VarName `vn` でプレフィックスします。

`PrefixContext(Val(:a), context)` は `PrefixContext(@varname(a), context)` と同等です。`context` が提供されていない場合、デフォルトで `DefaultContext()` になります。

このコンテキストは、パラメータの名前が一意であることを保証するために、ネストされたモデルで便利です。

参照: [`to_submodel`](@ref)
