```
connect_async(client::Client, connection::Connection)
```

Establishes an asynchronous connection to the MQTT broker using the provided `Client` and `Connection` objects. This function initializes the client, establishes the connection, and starts the necessary loops for communication.

# Arguments

  * `client::Client`: The MQTT client instance.
  * `connection::Connection`: The connection information used to connect to the broker.

# Returns

  * A `Future` object that can be used to await the completion of the connection process.

## Example

```julia
client, connection = MakeConnection("127.0.0.1", 1883; client_id="mqtt_client_1")
future = connect_async(client, connection)
wait(future)
```

# See Also

  * [`connect`](@ref): The synchronous version of this function.
