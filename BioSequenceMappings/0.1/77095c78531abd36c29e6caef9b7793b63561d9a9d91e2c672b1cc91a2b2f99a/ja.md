```
pairwise_frequencies(X::AbstractAlignment, w=X.weights; as_mat=false)
```

`q x q x L x L` テンソルを返します。 `(a, b, i, j)` 要素は、位置 `i` に `a` が、位置 `j` に `b` が見られる配列の割合です。

`as_mat=true` の場合、`q x q` ブロックが特定の2つの列間の相関を表す `qL x qL` 行列が返されます。
