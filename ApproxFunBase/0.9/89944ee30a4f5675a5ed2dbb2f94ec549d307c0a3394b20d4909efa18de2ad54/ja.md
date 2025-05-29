```
conversion_type(a::Space, b::Space)
```

`a`と`b`の両方にバンドされた[`Conversion`](@ref)演算子を持つ`Space`を返します。新しい`Conversion`演算子を追加する際は、`ApproxFun.conversion_rule`をオーバーライドしてください。

[`maxspace`](@ref)も参照してください。
