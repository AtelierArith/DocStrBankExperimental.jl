```
tensor_collinsgisin(p::Array, behaviour::Bool = false; correlation::Bool = false)
```

multipartite Bell 機能 `p` を Collins-Gisin 表記に変換します。`correlation` が `true` の場合、`p` は相関表記で書かれていると仮定されます。そうでない場合、`p` は確率表記で書かれていると仮定されます。`behaviour` が `true` の場合は、代わりに行動の変換を行います。正規化は仮定しません。

便利のために、`tensor_probability` の引数（状態と測定）も受け付けます。
