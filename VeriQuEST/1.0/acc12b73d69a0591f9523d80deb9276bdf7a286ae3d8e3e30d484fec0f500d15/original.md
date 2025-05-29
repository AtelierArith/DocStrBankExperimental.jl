```
get_ubqc_output(::Client, ::ComputationRound, mg::MetaGraphs.MetaGraph)
```

Gets the output of a computation round from a client's meta graph. The function checks if the round type of the meta graph is `TestRound`, and if so, it throws an error. Otherwise, it gets and returns the output of the computation round.

# Arguments

  * `::Client`: A `Client` instance.
  * `::ComputationRound`: A `ComputationRound` instance.
  * `mg::MetaGraphs.MetaGraph`: A client's meta graph.

# Returns

  * The output of the computation round.

# Errors

  * Throws an error if the round type of the meta graph is `TestRound`.

# Examples

```julia
ubqc_output = get_ubqc_output(Client(), ComputationRound(), mg)
```
