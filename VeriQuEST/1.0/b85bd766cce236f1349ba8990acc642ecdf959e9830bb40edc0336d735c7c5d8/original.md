```
get_output(::Client, ::Union{MBQC,ComputationRound}, mg)
```

Retrieves the output of a computation from a client's meta graph. The function gets the output indices from the meta graph, iterates over them, gets the outcome for each index, and stores the outcomes in a list. The list of outcomes is returned.

# Arguments

  * `::Client`: A `Client` instance.
  * `::Union{MBQC,ComputationRound}`: An instance of `MBQC` or `ComputationRound`.
  * `mg`: The client's meta graph.

# Returns

  * `Array`: An array of outcomes.

# Examples

```julia
mg = create_meta_graph(Client())
outcomes = get_output(Client(), ComputationRound(), mg)
```
