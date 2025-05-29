```
amqps_configure(;
    cacerts = nothing,
    verify = MbedTLS.MBEDTLS_SSL_VERIFY_NONE,
    client_cert = nothing,
    client_key = nothing
)
```

AMQPS接続を行うための設定を作成し、返します。

  * cacerts: 証明書検証に使用するCA証明書ファイル（またはその内容）。
  * verify: サーバー証明書を検証するかどうか。cacertsが提供されていない場合はデフォルトでfalse、提供されている場合はtrueです。
  * client*certおよびclient*key: 使用するクライアント証明書と対応する秘密鍵。デフォルトはnothing（クライアント証明書なし）。値はファイル名または証明書/鍵の内容のいずれかです。
