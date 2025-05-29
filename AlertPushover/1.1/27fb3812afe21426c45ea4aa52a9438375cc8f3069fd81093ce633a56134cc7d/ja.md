```
pushover_alert!(;token,user)
```

[Pushover](https://pushover.net) 通知サービスを使用して、`alert` を呼び出すときに通知を送信します。APIトークンとユーザートークンを提供する必要があり、これらは[PushoverのAPIの説明](https://pushover.net/api)に文書化されています。

引数なしでこの関数を呼び出すと、デフォルトのアラート通知バックエンドに戻ります。
