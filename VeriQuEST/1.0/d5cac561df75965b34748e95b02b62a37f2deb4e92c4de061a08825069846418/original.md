```
run_verification(client::Client, server::NoisyServer, round_types, client_resource, state_type)
```

Runs a verification process between a client and a noisy server. For each round type, it generates a property graph for the client, extracts the graph and quantum register from the client, creates resources for the server, runs the computation, initializes a blank quantum state for the server, and stores the client's meta graph. Returns a list of all client meta graphs.

# Arguments

  * `client::Client`: A `Client` instance participating in the verification process.
  * `server::NoisyServer`: A `NoisyServer` instance participating in the verification process.
  * `round_types`: The types of rounds to be run in the verification process.
  * `client_resource`: The resources available to the client.
  * `state_type`: The type of state used in the verification process.

# Returns

  * `Array`: An array of client meta graphs for each round type.

# Examples

```julia
client = Client()
server = NoisyServer(noise_model)
round_types = [ComputationRound(), TestRound()]
client_resource = create_resource(client, client_graph, client_qureg)
state_type = :state1
round_graphs = run_verification(client, server, round_types, client_resource, state_type)
```
