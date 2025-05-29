```
release_tcp_connection(
tcp_pool::TCPConnectionPool,
key::InetAddr,
connection::TCPSocket,
```

)

Release the given tcp `connection` indexed by the `key`. This will put the connection back to the pool.
