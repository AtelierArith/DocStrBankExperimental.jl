```
acquire_tcp_connection(tcp_pool::TCPConnectionPool, key::InetAddr)::Union{TCPSocket,Nothing}
```

プールからキー（IP+ポート）のためにtcp接続を取得します。プールがまだ閉じていない場合はTCPSocketを返し、そうでない場合は`nothing`が返されます。
