```
positional_encode(RandomWalkPE{K}, A)
```

Returns positional encoding (PE) of size `(K, N)` where N is node number. PE is generated by `K`-step random walk over given graph.

# Arguments

  * `K::Int`: First dimension of PE.
  * `A`: Adjacency matrix of a graph.

See also [`RandomWalkPE`](@ref) for random walk method.
