```
verify_rounds(::Client, ::TestRound, ::Terse, rounds_as_graphs, pass_threshold)
```

Verifies multiple rounds of computation from a list of client's meta graphs. The function iterates over the meta graphs, skips those with a round type of `ComputationRound`, verifies the round, and stores the outcome in a list. The function then counts the number of failed rounds. If the number of failed rounds is greater than the pass threshold, the function returns `Abort()`, otherwise it returns `Ok()`.

# Arguments

  * `::Client`: A `Client` instance.
  * `::TestRound`: A `TestRound` instance.
  * `::Terse`: A `Terse` instance.
  * `rounds_as_graphs`: A list of client's meta graphs.
  * `pass_threshold`: The threshold for a round to be considered as passed.

# Returns

  * `Abort` or `Ok`: `Abort()` if the number of failed rounds is greater than the pass threshold, `Ok()` otherwise.

# Examples

```julia
rounds_as_graphs = [create_meta_graph(Client()) for _ in 1:5]
pass_threshold = 3
round_verification = verify_rounds(Client(), TestRound(), Terse(), rounds_as_graphs, pass_threshold)
```
