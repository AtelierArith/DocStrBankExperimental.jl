```
unsubscribe(client::Client, topics::String...)
```

指定されたトピック名から`Client`インスタンスの購読を解除します。購読解除が完全に確認されるまで待機します。成功した場合は`nothing`を返し、失敗した場合は例外を返します。
