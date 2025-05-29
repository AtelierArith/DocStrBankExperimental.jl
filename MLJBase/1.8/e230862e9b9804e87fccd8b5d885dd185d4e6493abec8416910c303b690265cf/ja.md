```
nrows(X::AbstractNode)
```

新しいノード `N` を返します。`N() = nrows(X())` であり、`N(rows=rows) = nrows(X(rows=rows))` です。`X` のソースにあるデータの行数を取得するには、`nrows_at_source(X)` を使用します。
