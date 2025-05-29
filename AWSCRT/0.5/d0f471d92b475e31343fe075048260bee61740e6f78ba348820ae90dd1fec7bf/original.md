```
connect(
    connection::MQTTConnection,
    server_name::String,
    port::Integer,
    client_id::String;
    clean_session::Bool = true,
    on_connection_interrupted::Union{OnConnectionInterrupted,Nothing} = nothing,
    on_connection_resumed::Union{OnConnectionResumed,Nothing} = nothing,
    reconnect_min_timeout_secs::Integer = 5,
    reconnect_max_timeout_secs::Integer = 60,
    keep_alive_secs::Integer = 1200,
    ping_timeout_ms::Integer = 3000,
    protocol_operation_timeout_ms::Integer = 0,
    will::Union{Will,Nothing} = nothing,
    username::Union{String,Nothing} = nothing,
    password::Union{String,Nothing} = nothing,
    socket_options = Ref(aws_socket_options(AWS_SOCKET_STREAM, AWS_SOCKET_IPV6, 5000, 0, 0, 0, false)),
    alpn_list::Union{Vector{String},Nothing} = nothing,
    use_websockets::Bool = false,
    websocket_handshake_transform = nothing, # TODO union type
    proxy_options = nothing, # TODO union type
)
```

Open the actual connection to the server (async).

Arguments:

  * `connection (MQTTConnection)`: Connection to use.
  * `server_name (String)`: Server name to connect to.
  * `port (Integer)`: Server port to connect to.
  * `client_id (String)`: ID to place in CONNECT packet. Must be unique across all devices/clients. If an ID is already in use, the other client will be disconnected.
  * `clean_session (Bool) (default=true)`: Whether or not to start a clean session with each reconnect. If `true`, the server will forget all subscriptions with each reconnect. Set `false` to request that the server resume an existing session or start a new session that may be resumed after a connection loss. The `session_present` bool in the connection callback informs whether an existing session was successfully resumed. If an existing session is resumed, the server remembers previous subscriptions and sends mesages (with QoS level 1 or higher) that were published while the client was offline.
  * `on_connection_interrupted (Union{OnConnectionInterrupted,Nothing}) (default=nothing)`: Optional callback invoked whenever the MQTT connection is lost. The MQTT client will automatically attempt to reconnect. See [`OnConnectionInterrupted`](@ref).
  * `on_connection_resumed (Union{OnConnectionResumed,Nothing}) (default=nothing)`: Optional callback invoked whenever the MQTT connection is automatically resumed. See [`OnConnectionResumed`](@ref).
  * `reconnect_min_timeout_secs (Integer) (default=5)`: Minimum time to wait between reconnect attempts. Must be <= `reconnect_max_timeout_secs`. Wait starts at min and doubles with each attempt until max is reached.
  * `reconnect_max_timeout_secs (Integer) (default=60)`: Maximum time to wait between reconnect attempts. Must be >= `reconnect_min_timeout_secs`. Wait starts at min and doubles with each attempt until max is reached.
  * `keep_alive_secs (Integer) (default=1200)`: The keep alive value (seconds) to send in CONNECT packet. A PING will automatically be sent at this interval. The server will assume the connection is lost if no PING is received after 1.5X this value. This duration must be longer than `ping_timeout_ms`.
  * `ping_timeout_ms (Integer) (default=3000)`: Milliseconds to wait for ping response before client assumes the connection is invalid and attempts to reconnect. This duration must be shorter than `keep_alive_secs`.
  * `protocol_operation_timeout_ms (Integer) (default=0)`: Milliseconds to wait for a response to an operation that requires a response by the server. Set to zero to disable timeout. Otherwise, the operation will fail if no response is received within this amount of time after the packet is written to the socket. This works with PUBLISH (if QoS level > 0) and UNSUBSCRIBE.
  * `will (Union{Will,Nothing}) (default=nothing)`: Will to send with CONNECT packet. The will is published by the server when its connection to the client is unexpectedly lost.
  * `username (Union{String,Nothing}) (default=nothing)`: Username to connect with.
  * `password (Union{String,Nothing}) (default=nothing)`: Password to connect with.
  * `socket_options (Ref(aws_socket_options}) (default=Ref(aws_socket_options(AWS_SOCKET_STREAM, AWS_SOCKET_IPV6, 5000, 0, 0, 0, false)))`: Optional socket options.
  * `alpn_list (Union{Vector{String},Nothing}) (default=nothing)`: Connection-specific Application Layer Protocol Negotiation (ALPN) list. This overrides any ALPN list on the TLS context in the client this connection was made with. ALPN is not supported on all systems, see [`aws_tls_is_alpn_available`](https://octogonapus.github.io/LibAWSCRT.jl/dev/#LibAWSCRT.aws_tls_is_alpn_available-Tuple%7B%7D).
  * `use_websockets (Bool) (default=false)`: # TODO not implemented
  * `websocket_handshake_transform (nothing) (default=nothing)`: # TODO not implemented
  * `proxy_options (nothing) (default=nothing)`: # TODO not implemented

Returns a task which completes when the connection succeeds or fails.

If the connection succeeds, the task will contain a dict containing the following keys:

  * `:session_present`: `true` if resuming an existing session, `false` if new session

If the connection fails, the task will throw an exception.

!!! note
    All callbacks are run concurrently. Your callback implementations must be thread-safe. There is no concurrency limit.

