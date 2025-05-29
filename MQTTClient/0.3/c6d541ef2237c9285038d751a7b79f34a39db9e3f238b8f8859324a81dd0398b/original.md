```
Client
```

The MQTT client in Julia facilitates communication between a device and an MQTT broker over a network. It manages connections, message handling, and maintains the state of communication. The client operates through three main loops: the read loop listens for incoming messages from the broker and processes them using designated handlers; the write loop sends packets to the broker from a queue, ensuring thread safety with a socket lock; and the keep-alive loop periodically sends ping requests to the broker to maintain the connection and detect disconnections. This client uses atomic operations to ensure thread safety for shared variables and supports asynchronous task management for efficient, non-blocking operations.

# Fields

  * `state::UInt8`: client state.
  * `on_msg::TrieNode`: A trie mapping topics to callback functions.
  * `keep_alive::UInt16`: The keep-alive time in seconds.
  * `last_id::UInt16`: The last packet identifier used.
  * `in_flight::Dict{UInt16, Future}`: A dictionary mapping packet identifiers to futures.
  * `write_packets::AbstractChannel`: A channel for writing packets.
  * `socket`: The socket used for communication with the broker.
  * `socket_lock`: A lock for synchronizing access to the socket.
  * `ping_timeout::UInt64`: The ping timeout in seconds.
  * `ping_outstanding::Atomic{UInt8}`: An atomic counter for the number of outstanding ping requests.
  * `last_sent::Atomic{Float64}`: An atomic float representing the timestamp of the last sent packet.
  * `last_received::Atomic{Float64}`: An atomic float representing the timestamp of the last received packet.

# Constructor

`Client(ping_timeout::UInt64=UInt64(60))` constructs a new `Client` object with the specified ping timeout (default: 60 seconds).
