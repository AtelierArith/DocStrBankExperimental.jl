```
update_measurement(client::Client, round::Union{MBQC, TestRound}, q, mg, outcome)
```

This function is used in the context of Measurement-Based Quantum Computing (MBQC) or during a test round.  It takes an outcome and simply returns it without making any modifications.

# Arguments

  * `client::Client`: The client for which the measurement is being updated.
  * `round::Union{MBQC, TestRound}`: Specifies whether the computation round is a part of MBQC or a test round.
  * `q`: The qubit for which the measurement is being updated.
  * `mg`: The measurement graph associated with the computation round.
  * `outcome`: The outcome of the measurement.

# Returns

  * The same `outcome` that was passed as an argument.

# Examples

```julia
client = Client()
round = MBQC()
q = 1
mg = MeasurementGraph()
outcome = 0
update_measurement(client, round, q, mg, outcome)
```
