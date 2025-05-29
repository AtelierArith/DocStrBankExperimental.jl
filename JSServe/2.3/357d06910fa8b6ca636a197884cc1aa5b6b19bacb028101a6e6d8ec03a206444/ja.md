```
configure_server!(;
        listen_url::String=SERVER_CONFIGURATION.listen_url[],
        listen_port::Integer=SERVER_CONFIGURATION.listen_port[],
        forwarded_port::Integer=listen_port,
        proxy_url=nothing,
        content_delivery_url=nothing
    )
```

自動的に起動されるサーバーのパラメータを設定します。

```
Parameters:

* listen_url=SERVER_CONFIGURATION.listen_url[]
    サーバーがリッスンするアドレスです。
    0.0.0.0、127.0.0.1、::、::1、またはlocalhostでなければなりません。
    ENV変数で異なる設定がされていない場合、デフォルトは127.0.0.1になります。

* listen_port::Integer=SERVER_CONFIGURATION.listen_port[],
    デフォルトのサーバーがリッスンするポートです。
    ENV変数で異なる設定がされていない場合、デフォルトは9384になります。

* forwarded_port::Integer=listen_port,
    ポートが他のポートに転送される場合、ここに設定してください！

* proxy_url=nothing
    サーバーにアクセス可能なURLです。
    "127.0.0.1"で提供される場合、これはhttp://localhost:forwarded_portにデフォルト設定されます。
    listen_urlが"0.0.0.0"の場合、これはhttp://$(Sockets.getipaddr()):forwarded_portにデフォルト設定され、
    サーバーがローカルネットワーク内でアクセス可能になります。
    サーバーが外部のDNSサーバーからアクセス可能である必要がある場合、
    ここに設定する必要があります。
```
