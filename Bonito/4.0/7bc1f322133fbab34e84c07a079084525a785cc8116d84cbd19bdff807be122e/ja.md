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
パラメータ:

* listen_url=SERVER_CONFIGURATION.listen_url[]
    サーバーがリッスンするアドレス。
    0.0.0.0、127.0.0.1、::、::1、またはlocalhostでなければなりません。
    ENV変数で異なる設定がされていない場合、デフォルトは127.0.0.1になります。

* listen_port::Integer=SERVER_CONFIGURATION.listen_port[],
    デフォルトのサーバーがリッスンするポート。
    ENV変数で異なる設定がされていない場合、デフォルトは9384になります。

* forwarded_port::Integer=listen_port,
    ポートが他のポートに転送される場合、ここに設定してください！

* proxy_url=nothing
    サーバーにアクセス可能なURLで、BonitoのHTMLでリソースを宣言し、WebSocket接続を確立するために使用されます。
    `""`または`nothing`に設定すると、サーバーがリッスンするURLが使用されます。
    したがって、`listen_url="127.0.0.1"`の場合、これはhttp://localhost:forwarded_port（`local_url(server, "")`と同じ）にデフォルト設定されます。
    また、相対URLを使用するために`"."`に設定することもできます。例えば、ローカルネットワーク上でウェブページにアクセスする場合や、自分のサーバーでオンラインで提供する場合です。
    これは、ページがどこで提供されるかを事前に知らない場合にBonitoを介してウェブサイト全体を提供するための推奨オプションです。
    もしより複雑な場合、例えばHTMLがBonitoサーバーにプロキシを通すURLとは異なるURLで提供される場合は、
     完全なURLを設定する必要があります。例えば、`proxy_url=https://bonito.makie.org`のように。
```
