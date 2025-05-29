```
Connection{T <: AbstractIOConnection}
```

The `Connection` struct in Julia encapsulates the configuration and connection details required for an MQTT client to connect to an MQTT broker. This struct supports two types of connection protocols: TCP and Unix Domain Sockets (UDS), both of which are subtypes of `AbstractIOConnection`. The struct includes fields for protocol type, keep-alive interval, client ID, user credentials, a will message (a message that is sent by the broker if the client disconnects unexpectedly), and a flag indicating whether the session is clean (i.e., no persistent session state). The `Connection` constructor allows for flexible instantiation with default or specified values for each field, enabling easy setup of connection parameters tailored to the specific requirements of the MQTT client and broker interaction.

## Fields

  * `protocol::T`: The underlying IO connection.
  * `keep_alive::Int64`: The keep-alive time in seconds.
  * `client_id::String`: The client identifier.
  * `user::User`: The user credentials.
  * `will::Message`: The last will and testament message.
  * `clean_session::Bool`: Whether to start a clean session.

## Constructors

`Connection(protocol::T; keep_alive::Int64=32, client_id::String=randstring(8), user::User=User("", ""), will::Message=Message(false, 0x00, false, "", UInt8[]), clean_session::Bool=true) where T <: AbstractIOConnection` constructs a new `Connection` object with the specified protocol and optional keyword arguments.

`Connection(protocol::T, keep_alive::Int64, client_id::String, user::User, will::Message, clean_session::Bool) where T <: AbstractIOConnection` constructs a new `Connection` object with the specified arguments.

### Example using TCP protocol with default and custom values

```julia
tcp_connection = Connection(
    TCP(Sockets.localhost, 1883);       # Using TCP with localhost and port 1883
    keep_alive=60,                      # Custom keep-alive interval of 60 seconds
    client_id="my_mqtt_client",         # Custom client ID
    user=User("username", "password"),  # Custom user credentials
    will=Message(false, 0x01, false, "last/will/topic", UInt8[]),  # Custom will message
    clean_session=true,                  # Default clean session flag
)
```

### Example using UDS protocol with all custom values

```julia
uds_connection_full = Connection(
    UDS("/var/run/mqtt.sock"),          # Using UDS with specified socket path
    45,                                 # Custom keep-alive interval of 45 seconds
    "another_client",                   # Custom client ID
    User("user", "pass"),               # Custom user credentials
    Message(true, 0x00, true, "will/topic", UInt8[1, 2, 3]),  # Custom will message
    false,                               # Custom clean session flag
)
```
