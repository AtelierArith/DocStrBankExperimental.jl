```
MakeConnection(host::Union{IPAddr, String}, port::Int64;
               ping_timeout=UInt64(60),
               keep_alive::Int64=32,
               client_id::String=randstring(8),
               user::User=User("", ""),
               will::Message=Message(false, 0x00, false, "", UInt8[]),
               clean_session::Bool=true)::Tuple

MakeConnection(path::String;
               ping_timeout=UInt64(60),
               keep_alive::Int64=32,
               client_id::String=randstring(8),
               user::User=User("", ""),
               will::Message=Message(false, 0x00, false, "", UInt8[]),
               clean_session::Bool=true)::Tuple
```

Creates an MQTT client connection to an MQTT broker, handling the construction of both the `Client` and `Connection` objects inside the `Configuration` struct. This function provides flexible ways to specify the connection details either through a TCP connection with host and port, a Unix Domain Socket path.

# Arguments

  * `host::Union{IPAddr, String}`: The IP address or hostname of the MQTT broker.
  * `port::Int64`: The port number to connect to.
  * `path::String`: The file system path for Unix Domain Socket connection.
  * `io::T`: An object of subtype `AbstractIOConnection`.
  * `ping_timeout::UInt64`: The ping timeout in seconds (default: 60).
  * `keep_alive::Int64`: The keep-alive time in seconds (default: 32).
  * `client_id::String`: The client identifier (default: a random string of length 8).
  * `user::User`: The user credentials for the MQTT broker (default: anonymous user).
  * `will::Message`: The last will message to be sent in case of unexpected disconnection (default: an empty will message).
  * `clean_session::Bool`: Indicates whether to start a clean session (default: true).

# Returns

  * A `Configuration` struct where `client::Client` is the MQTT client instance and `connection::Connection` is the connection information used to connect to the broker.

This function simplifies the process of setting up an MQTT client connection. Depending on the type of connection, you can specify the broker's IP address and port or a Unix Domain Socket path, it infers the Protocol and then constructs the necessary provided or default parameters. Refer to the documentation for [`Client`](@ref) and [`Connection`](@ref) object.

## Examples

```julia
# Example with IP address and port
client, connection = MakeConnection("127.0.0.1", 1883; client_id="mqtt_client_1")

# Example with Unix Domain Socket path
client, connection = MakeConnection("/var/run/mqtt.sock"; user=User("user", "pass"))
```
