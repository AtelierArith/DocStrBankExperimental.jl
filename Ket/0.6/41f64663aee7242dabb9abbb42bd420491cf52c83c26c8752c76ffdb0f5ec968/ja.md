```
tensor_correlation(p::AbstractArray, behaviour::Bool = false; collinsgisin::Bool = false, marg::Bool = true)
```

multipartite Bell functional `p` を相関表記に変換します。`collinsgisin` が `true` の場合、`p` はコリンズ-ギジン表記で書かれていると仮定されます。そうでない場合、`p` は確率表記で書かれていると仮定されます。`marg` が `false` の場合、出力には完全な相関関数のみが含まれ、周辺は含まれません。`behaviour` が `true` の場合、行動の変換を行います。正規化は仮定しません。

便利のために、`tensor_probability` の引数（状態と測定）も受け付けます。
