```
verify_rounds(::Client, ::ComputationRound, ::Verbose, rounds_as_graphs)
```

Verifies multiple rounds of computation from a list of client's meta graphs. The function counts the number of computation rounds, collects the outputs of the computation rounds, calculates the mode of the outputs, and counts the number of outputs that match the mode. The function then returns a tuple with the number of failed and passed rounds.

# Arguments

  * `::Client`: A `Client` instance.
  * `::ComputationRound`: A `ComputationRound` instance.
  * `::Verbose`: A `Verbose` instance.
  * `rounds_as_graphs`: A list of client's meta graphs.

# Returns

  * `Tuple`: A tuple with the number of failed and passed rounds.

# Examples

```julia
rounds_as_graphs = [create_meta_graph(Client()) for _ in 1:5]
round_verification = verify_rounds(Client(), ComputationRound(), Verbose(), rounds_as_graphs)
```
