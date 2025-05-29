```
list_indexes(context::PineconeContext)
```

指定されたアカウントのインデックスをリストするJSON配列を返します。これは、渡されたPineconeContextインスタンスによって示されます。

# 例

```julia-repl
julia> context = Pinecone.init("asdf-1234-zyxv", "us-west1-gcp")
Pinecone.list_indexes(context)
["example-index", "filter-example"]
```
