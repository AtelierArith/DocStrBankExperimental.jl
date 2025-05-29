```
overapproximate(X::LazySet{N}, dirs::AbstractDirections;
                [prune]::Bool=true) where {N}
```

テンプレート方向を用いて（おそらく無限大の）集合を過大評価します。

### 入力

  * `X`     – 集合
  * `dirs`  – 方向
  * `prune` – （オプション、デフォルト: `true`）冗長な制約を削除するためのフラグ

### 出力

集合 `X` を `dirs` からの方向で過大評価する多面体。過大評価はサポート関数を使用して計算されます。結果は、制約が有界であれば `HPolytope` となり、そうでなければ `HPolyhedron` となります。
