```
update_measurement(client::Client, round::ComputationRound, q, mg, outcome)
```

Update the measurement for a given computation round and qubit. The function retrieves the one-time pad integer  associated with the qubit and computes the absolute difference between the outcome and the one-time pad integer.

# Arguments

  * `client::Client`: The client for which the measurement is being updated.
  * `round::ComputationRound`: The computation round for which the measurement is being updated.
  * `q`: The qubit for which the measurement is being updated.
  * `mg`: The measurement graph associated with the computation round.
  * `outcome`: The outcome of the measurement.

# Returns

  * The absolute difference between the outcome and the one-time pad integer.

# Examples

```julia
client = Client()
round = ComputationRound()
q = 1
mg = MeasurementGraph()
outcome = 0
update_measurement(client, round, q, mg, outcome)
```
