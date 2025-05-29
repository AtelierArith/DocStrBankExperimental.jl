```
IntervalSimplex <: AbstractSimplex

IntervalSimplex(p::Int, q::Int)
IntervalSimplex()
```

単純体間隔（1-単純体）を表す型です。単純体間隔における `n`-単純体は、`p+q-1` が `n` に等しい2つの非負整数 `p` と `q` によって決定されます。

上記の最初のコンストラクタは、`p` 頂点が `0` に等しく、`q` 頂点が `1` に等しい `p+q-1`-単純体を返します。2番目のコンストラクタは `SimplicialInterval(1, 1)` の短縮形であり、唯一の非退化 `1`-単純体を返します。
