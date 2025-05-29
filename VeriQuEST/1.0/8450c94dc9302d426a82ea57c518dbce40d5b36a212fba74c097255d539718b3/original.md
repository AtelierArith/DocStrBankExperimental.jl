```
clone_qureq(::Server,client_qureg,env)
```

Creates a clone of a quantum register in the context of a server.

# Arguments

  * `::Server`: Indicates that this function is used in the context of a server.
  * `client_qureg`: The quantum register to be cloned.
  * `env`: The QuEST environment in which the quantum register is cloned.

# Examples

```julia
clone_qureq(Server(),client_qureg,env)
```
