```
overapproximate(X::LazySet{N}, dirs::Type{<:AbstractDirections}) where {N}
```

テンプレート方向で集合を過大評価します。

### 入力

  * `X`    – 集合
  * `dirs` – 方向表現の型

### 出力

集合 `X` を `dirs` からの方向で過大評価する多面体。結果は有界であれば `HPolytope` であり、そうでなければ `HPolyhedron` です。
