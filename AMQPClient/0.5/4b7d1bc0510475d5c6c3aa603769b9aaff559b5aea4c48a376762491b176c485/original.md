```
connection(f; kwargs...)

connection(;
    virtualhost = "/",
    host = "localhost",
    port = AMQPClient.AMQP_DEFAULT_PORT,
    framemax = 0,
    heartbeat = true,
    keepalive = DEFAULT_KEEPALIVE_SECS,
    send_queue_size = CONN_MAX_QUEUED,
    auth_params = AMQPClient.DEFAULT_AUTH_PARAMS,
    channelmax = AMQPClient.DEFAULT_CHANNELMAX,
    connect_timeout = AMQPClient.DEFAULT_CONNECT_TIMEOUT,
    amqps = nothing
)
```

Creates a fresh connection to the AMQP server. Returns a connection that can be used to open channels subsequently. Can be used with the Julia do block syntax to create a connection and close it afterwards.

Keyword arguments:

  * `host`: The message server host to connect to. Defaults to "localhost".
  * `port`: The message server port to connect to. Defaults to the default AMQP port.
  * `virtualhost`: The virtual host to connect to. Defaults to "/".
  * `amqps`: If connection is to be done over AMQPS, the TLS options to use. See `amqps_configure`.
  * `connect_timeout`: TCP connect timeout to impose. Default `AMQPClient.DEFAULT_CONNECT_TIMEOUT`,
  * `framemax`: The maximum frame size to use. Defaults to 0, which means no limit.
  * `heartbeat`: `true` to enable heartbeat, `false` to disable. Can also be set to a positive integer,   in which case it is the heartbeat interval in seconds. Defaults to `true`. If `false`, ensure    `keepalive` is enabled to detect dead connections. This parameter is negotiated with the server.
  * `keepalive`: `true` to enable TCP keepalives, `false` to disable. Can also be set to a positive integer,   in which case it is the keepalive interval in seconds. Defaults to `DEFAULT_KEEPALIVE_SECS`.
  * `send_queue_size`: Maximum number of items to buffer in memory before blocking the send API until   messages are drained. Defaults to CONN*MAX*QUEUED.
  * `auth_params`: Parameters to use to authenticate the connection. Defaults to AMQPClient.DEFAULT*AUTH*PARAMS.
  * `channelmax`: Maximum channel number to impose/negotiate with the server. Defaults to AMQPClient.DEFAULT_CHANNELMAX.
