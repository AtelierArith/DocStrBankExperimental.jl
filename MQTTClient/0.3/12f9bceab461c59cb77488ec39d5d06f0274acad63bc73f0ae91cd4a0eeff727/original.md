```
IOConnection(ip::IPAddr, port::Int64)
```

Constructs a new `TCP` object with the specified IP address and port number.

# Arguments

  * `ip::IPAddr`: The IP address of the remote host.
  * `port::Int64`: The port number on the remote host.

# Returns

  * `TCP`: A new `TCP` object.
  *   *   *

    IOConnection(ip::String, port::Int64)

Constructs a new `TCP` object with the specified IP address and port number.

# Arguments

  * `ip::String`: The IP address of the remote host as a string.
  * `port::Int64`: The port number on the remote host.

# Returns

  * `TCP`: A new `TCP` object.
  *   *   *

    IOConnection(path::AbstractString)

Constructs a new `UDS` object with the specified file system path.

# Arguments

  * `path::AbstractString`: The file system path of the socket.

# Returns

  * `UDS`: A new `UDS` object.
