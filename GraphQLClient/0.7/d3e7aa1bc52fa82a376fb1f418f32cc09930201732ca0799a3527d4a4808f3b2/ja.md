```
get_queries(client::Client)
```

GraphQLサーバーから利用可能なすべてのクエリを返します。イントロスペクションが実行されていない場合は、`full_introspection!(client)`を実行します。
