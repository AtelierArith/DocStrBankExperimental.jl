```
BatchIterator(X; batchsize = nothing, limit=size(X,2))
```

`X`の`batchsize`列のバッチを反復処理するためのラッパー。`X`は`size`と2dインデックスをサポートする任意の型であることができます。`limit`が指定されている場合、反復処理は`X[:, 1:limit]`の列に制限されます。
