```
verify_rounds(::Client, ::TestRound, ::Verbose, rounds_as_graphs, pass_threshold)
```

Verifies multiple rounds of computation from a list of client's meta graphs. The function iterates over the meta graphs, skips those with a round type of `ComputationRound`, verifies the round, and stores the outcome in a list. The function then counts the number of failed rounds and returns a tuple with the number of failed and passed rounds.

# Arguments

  * `::Client`: A `Client` instance.
  * `::TestRound`: A `TestRound` instance.
  * `::Verbose`: A `Verbose` instance.
  * `rounds_as_graphs`: A list of client's meta graphs.
  * `pass_threshold`: The threshold for a round to be considered as passed.

# Returns

  * `Tuple`: A tuple with the number of failed and passed rounds.

# Examples

```julia
rounds_as_graphs = [create_meta_graph(Client()) for _ in 1:5]
pass_threshold = 3
round_verification = verify_rounds(Client(), TestRound(), Verbose(), rounds_as_graphs, pass_threshold)
```
