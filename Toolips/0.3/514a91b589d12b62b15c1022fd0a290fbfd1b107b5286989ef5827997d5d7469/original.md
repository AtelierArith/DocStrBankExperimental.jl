```julia
abstract type AbstractConnection
```

An `AbstractConnection` is how a server interacts with each client on an individual basis.  Variations of the `Connection` are passed to routes as their only argument. The `Connection`

  * Can be written to with `write!`
  * Contains client data accessible with *getter* functions, such as `get_ip`.
  * See also: `start!`, `route`, `route!`, `Connection`, `get_ip`, `get_args`
