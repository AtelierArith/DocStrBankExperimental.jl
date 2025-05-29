```
MQTTClient(
    tls_ctx::Union{ClientTLSContext,Nothing},
    bootstrap::ClientBootstrap = get_or_create_default_client_bootstrap(),
)
```

MQTTクライアント。

引数:

  * `tls_ctx (Union{ClientTLSContext,Nothing})`: セキュアソケット接続のためのTLSコンテキスト。`nothing`の場合、暗号化されていない接続が使用されます。
  * `bootstrap (ClientBootstrap) (default=get_or_create_default_client_bootstrap())`: 新しいソケット接続を開始する際に使用するクライアントブートストラップ。デフォルトではシングルトンが使用されます。
