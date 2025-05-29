```
connect(client::Client, connection::Connection)
```

Establishes a synchronous connection to the MQTT broker using the provided [`Client`](@ref) and [`Connection`](@ref) objects. This function wraps [`connect_async`](@ref) and waits for the connection process to complete.

# Arguments

  * `client::Client`: The MQTT client instance.
  * `connection::Connection`: The connection information used to connect to the broker.

# Returns

  * The result of the connection process after it completes.

The connect function is responsible for establishing a connection between an MQTT client and an MQTT broker. It initializes the client's state, sets up the necessary communication channels, and handles the connection handshake according to the MQTT protocol. When called, connect first ensures that the client's state and resources are properly initialized. This includes resetting the client's state, setting up the socket connection, and creating the channels and locks required for communication. The function then starts the asynchronous tasks needed to manage the read, write, and keep-alive loops, which are crucial for maintaining the connection and ensuring that messages are sent and received properly.

Additionally, the connect function handles the specifics of the MQTT protocol handshake. It constructs and sends the CONNECT packet, including details such as the client ID, user credentials, and optional will message. This handshake process ensures that the broker recognizes the client and sets up the session according to the specified parameters. The synchronous connect function blocks until the connection process is complete, providing a straightforward way to establish the connection without needing to manage asynchronous operations directly. This makes it suitable for applications that require a simple, blocking call to connect to the broker and start communicating immediately.

## Example

```julia
client, connection = MakeConnection("127.0.0.1", 1883; client_id="mqtt_client_1")
result = connect(client, connection)
```

# See Also

  * [`connect_async`](@ref): The asynchronous version of this function.
  * [`Client`](@ref)
  * [`Connection`](@ref)
