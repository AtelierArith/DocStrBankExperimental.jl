```
request!(s, r, quantity, request)
request!(s, q, request)
```

`SimResource`または`SimQueue`からのリソースのリクエストを登録するために使用される関数。

`SimResource`では、要求された`quantity`を提供する必要があり、`request`は`Scheduler`引数のみを受け入れます（何を望んでいるかを知っている必要があります）。返されるタプルは次のとおりです：

  * 成功した場合は`true`、リクエストが多すぎた場合は`false`
  * 作成された`ResourceRequest`オブジェクト

`SimResource`の関数`request`は、1つの引数`Scheduler`を受け入れる必要があります。`SimQueue`の関数`request`は、2つの引数`Scheduler`とオブジェクトを受け入れる必要があります。
