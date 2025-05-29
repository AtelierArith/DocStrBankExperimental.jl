```
query_requires_relayout(daf::DafReader, query::QueryString)::Bool
```

`daf` データの `query` を計算するために [`relayout!`](@ref) のいずれかの行列が必要かどうか。これにより、クエリが構文的に有効であり、クエリを計算できることも確認されますが、無効な値や型のために特定のデータに適用すると失敗する可能性があります。
