```
create_resource(::Server,client_graph,client_qureg)
```

Creates a resource in the context of a server.

# Arguments

  * `::Server`: Indicates that this function is used in the context of a server.
  * `client_graph`: The graph to be copied/cloned.
  * `client_qureg`: The quantum register to be copied/cloned.

# Examples

```julia
create_resource(Server(),client_graph,client_qureg)
```
