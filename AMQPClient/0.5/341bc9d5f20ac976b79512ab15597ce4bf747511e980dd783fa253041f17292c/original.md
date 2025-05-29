```
channel(conn, id, create)
channel(f, args...)
```

Create or return an existing a channel object. Multiple channels can be multiplexed over a single connection. Can be used with the Julia do block syntax to create a channel and close it afterwards.

  * `conn`: The connection over which to create the channel.
  * `id`: Channels are identified by their numeric id. Specifying `AMQPClient.UNUSED_CHANNEL` as channel   id during creation will automatically assign an unused id.
  * `create`: If true, a new channel will be created. Else an existing channel with the specified id   will be returned.
