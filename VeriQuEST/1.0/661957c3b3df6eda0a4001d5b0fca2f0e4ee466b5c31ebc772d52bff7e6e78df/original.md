```
verify_rounds(::Client, ::ComputationRound, ::Terse, rounds_as_graphs)
```

Verifies multiple rounds of computation from a list of client's meta graphs. The function counts the number of computation rounds, collects the outputs of the computation rounds, calculates the mode of the outputs, and counts the number of outputs that match the mode. If the number of outputs that match the mode is greater than half the number of computation rounds, the function returns `Ok()`, otherwise it returns `Abort()`.

# Arguments

  * `::Client`: A `Client` instance.
  * `::ComputationRound`: A `ComputationRound` instance.
  * `::Terse`: A `Terse` instance.
  * `rounds_as_graphs`: A list of client's meta graphs.

# Returns

  * `Ok` or `Abort`: `Ok()` if the number of outputs that match the mode is greater than half the number of computation rounds, `Abort()` otherwise.

# Examples

```julia
rounds_as_graphs = [create_meta_graph(Client()) for _ in 1:5]
round_verification = verify_rounds(Client(), ComputationRound(), Terse(), rounds_as_graphs)
```
