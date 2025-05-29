```
LocalInteraction(payoff_matrix,
                 adj_matrix[, revision=SimultaneousRevision()])
```

Construct a `LocalInteraction` instance.

# Arguments

  * `payoff_matrix::Matrix` : The payoff matrix of the game.
  * `adj_matrix::AbstractMatrix` : Adjacency matrix of the graph in the model.
  * `revision::AbstractRevision` : Arguments to specify the revision method. `SimultaneousRevision()` or `AsynchronousRevision`

# Returns

  * `::LocalInteraction` : The local interaction model.
