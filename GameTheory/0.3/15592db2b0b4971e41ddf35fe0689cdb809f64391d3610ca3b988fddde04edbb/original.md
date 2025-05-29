```
LocalInteraction(g, adj_matrix[, revision=SimultaneousRevision()])
```

Construct a `LocalInteraction` instance.

# Arguments

  * `g::NormalFormGame` : The game used in the model.
  * `adj_matrix::AbstractMatrix` : Adjacency matrix of the graph in the model.
  * `revision::AbstractRevision` : Arguments to specify the revision method; `SimultaneousRevision()` or `AsynchronousRevision()`.

# Returns

  * `::LocalInteraction` : The local interaction model.
