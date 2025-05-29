```
absuri(uri::Union{URI,AbstractString}, context::Union{URI,AbstractString}) -> URI
```

`uri.path` と `uri.query` を使用して絶対URIを構築し、他のコンポーネントは `context` から埋めます。
