```
clone_graph(::Server,client_graph)
```

Creates a clone of a graph in the context of a server.

# Arguments

  * `::Server`: Indicates that this function is used in the context of a server.
  * `client_graph`: The graph to be cloned.

# Examples

```julia
clone_graph(Server(),client_graph)
```
