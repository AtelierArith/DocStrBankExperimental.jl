```
run_verification(::Client, ::Server, round_types, client_resource, state_type)
```

Runs a verification process between a client and a server. For each round type, the function generates a client meta graph, extracts the graph and quantum register (qureg) from the client, creates server resources, runs a computation, initializes a blank quantum state on the server, and stores the client meta graph in a list. The list of client meta graphs is returned.

# Arguments

  * `::Client`: A `Client` instance.
  * `::Server`: A `Server` instance.
  * `round_types`: The types of rounds to run.
  * `client_resource`: The client's resources.
  * `state_type`: The type of state.

# Returns

  * `Array`: An array of client meta graphs.

# Examples

```julia
round_types = ["round1", "round2"]
client_resource = create_resource(Client())
state_type = "state_type_example"
round_graphs = run_verification(Client(), Server(), round_types, client_resource, state_type)
```
