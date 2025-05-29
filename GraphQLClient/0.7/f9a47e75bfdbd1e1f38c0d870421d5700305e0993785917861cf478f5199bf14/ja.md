```
get_subscriptions(client::Client)
```

GraphQLサーバーから利用可能なすべてのサブスクリプションを返します。イントロスペクションが実行されていない場合は、`full_introspection!(client)`を実行します。
