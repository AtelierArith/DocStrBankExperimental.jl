```
LocalInteraction{N, T, S, A, TR}
```

Type representing the local interaction model with N players.

# Fields

  * `players::NTuple{N,Player{2,T}}` : Tuple of `Player` instances.
  * `num_actions::Integer` : The number of actions for players.
  * `adj_matrix::Array{S,2}` : Adjacency matrix of the graph in the model.
  * `revision<:AbstractRevision` : The way to revise the action profile.
