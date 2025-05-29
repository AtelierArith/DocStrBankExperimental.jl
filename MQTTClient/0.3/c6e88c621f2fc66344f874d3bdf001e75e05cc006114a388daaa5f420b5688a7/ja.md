```
unsubscribe_async(client::Client, topics::String...)
```

指定されたトピック名から`Client`インスタンスの購読を解除します。コールバックをクライアントから削除します。成功した場合は`nothing`を含む`Future`オブジェクトを返し、失敗した場合は例外を返します。
