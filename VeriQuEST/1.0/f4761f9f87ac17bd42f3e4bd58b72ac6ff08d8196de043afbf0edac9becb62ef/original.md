```
entangle_graph!(::Server,qureg,graph)
```

Entangles a quantum register with a graph in the context of a server.

# Arguments

  * `::Server`: Indicates that this function is used in the context of a server.
  * `qureg`: The quantum register to be entangled.
  * `graph`: The graph with which the quantum register is entangled.

# Examples

```julia
entangle_graph!(Server(),qureg,graph)
```
