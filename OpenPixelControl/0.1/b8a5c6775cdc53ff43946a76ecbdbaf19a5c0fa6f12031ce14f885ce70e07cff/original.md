```
OpenPixelConnection
```

A struct containing all necessary information for the status of the OPC connection.

This for now only requires the one field

  * `connection` which is a `TCPSocket`.

# Constructors

  * `OpenPixelConnection()` – generates a connection to `localhost:7890`
  * `OpenPixelConnection(port)` – generates a connection to `localhost:port`
  * `OpenPixelConnection(host,port)` – generates a connection ho `host:port`
