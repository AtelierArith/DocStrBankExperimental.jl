```
get_mutations(client::Client)
```

GraphQLサーバーから利用可能なすべてのミューテーションを返します。イントロスペクションが実行されていない場合は、`full_introspection!(client)`を実行します。
