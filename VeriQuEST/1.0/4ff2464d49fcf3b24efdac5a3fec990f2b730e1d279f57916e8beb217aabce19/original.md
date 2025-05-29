```
update_measurement(client::Client, q, mg, outcome)
```

This function retrieves the round type from the measurement graph and then calls the `update_measurement` function  with the client, round type, qubit, measurement graph, and outcome as arguments.

# Arguments

  * `client::Client`: The client for which the measurement is being updated.
  * `q`: The qubit for which the measurement is being updated.
  * `mg`: The measurement graph associated with the computation round.
  * `outcome`: The outcome of the measurement.

# Returns

  * The result of calling `update_measurement` with the client, round type, qubit, measurement graph, and outcome.

# Examples

```julia
client = Client()
q = 1
mg = MeasurementGraph()
outcome = 0
update_measurement(client, q, mg, outcome)
```
