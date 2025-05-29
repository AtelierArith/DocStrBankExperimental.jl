```
B = block_diag(As::LinearMapAX... ; tryop::Bool)
```

ブロックからブロック対角の `LinearMapAX` オブジェクトを作成します。

`tryop` が `true` で、すべてのブロックが同じ `idim` と `odim` を持たない限り、`LinearMapAM` を返します。

`tryop` のデフォルトは、すべてのブロックが `LinearMapAO` 型である場合は `true` です。
