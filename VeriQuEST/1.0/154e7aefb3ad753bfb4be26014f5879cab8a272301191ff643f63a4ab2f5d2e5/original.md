```
get_mode_output(::Client, ::ComputationRound, rounds_as_graphs::Vector)
```

Collects the outputs of computation rounds from a list of client's meta graphs and returns the mode of the outputs. The function iterates over the meta graphs, skips those with a round type of `TestRound`, gets the output of the computation round, and stores it in a list. The function then calculates and returns the mode of the outputs.

# Arguments

  * `::Client`: A `Client` instance.
  * `::ComputationRound`: A `ComputationRound` instance.
  * `rounds_as_graphs::Vector`: A list of client's meta graphs.

# Returns

  * `mode(outputs)`: The mode of the outputs.

# Examples

```julia
rounds_as_graphs = [create_meta_graph(Client()) for _ in 1:5]
mode_output = get_mode_output(Client(), ComputationRound(), rounds_as_graphs)
```
