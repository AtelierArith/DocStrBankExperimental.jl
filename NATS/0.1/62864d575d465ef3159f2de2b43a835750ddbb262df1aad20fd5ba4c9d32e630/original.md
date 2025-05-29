```julia
reconnect(connection; should_wait)

```

Force a connection reconnect. If connection is `CONNECTED` this will close it and reopen again resubscribing all existing subscriptions. If connection is `DISCONNECTED` it will try to connect with all previously existing subscription restored. In case connection is already `CONNECTING` this method have no effect. If called on connection that is `DRAINING` or `DRAINED` error will be thrown.

During reconnect period some messages both published and received by the connection might be lost.

Optional keyword aruguments:

  * `should_wait`: If `true` method will block until reconnection process is started, default is `true`.
