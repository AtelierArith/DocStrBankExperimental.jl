```
create_quantum_env(client::Client)
```

Create a new quantum environment using the QuEST environment creation function.

# Arguments

  * `client::Client`: The client for which the quantum environment is being created.

# Returns

  * A new quantum environment.

# Examples

```julia
client = Client()
env = create_quantum_env(client)
```
