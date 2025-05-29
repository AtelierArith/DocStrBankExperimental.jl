```
release_tcp_connection(
tcp_pool::TCPConnectionPool,
key::InetAddr,
connection::TCPSocket,
```

)

指定された `key` でインデックスされた tcp `connection` を解放します。これにより、接続がプールに戻されます。
