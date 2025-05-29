```
acquire_tcp_connection(tcp_pool::TCPConnectionPool, key::InetAddr)::Union{TCPSocket,Nothing}
```

Acquire a tcp connection from the pool for the key (IP+Port). Return a TCPSocket if the pool is not closed yet, otherwise `nothing` will be returned
