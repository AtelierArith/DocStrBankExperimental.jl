```
Board(id::Integer)
```

Generate a representation of a go board graph with the given `id`. The number of nodes is the smallest `n` such that `2^(n*(n-1)/2)>id`. The edges are found in the following way:

  * Enumerate all potential edges in the order `(1,2), (1,3), ..., (1,n), (2,3), (2,4), ..., (2,n), ..., (n,n)`.
  * Convert `id` to binary with `n*(n-1)/2` digits.
  * The edges in the list matching ones in the binary sequence are included in the graph.

Note: Many of these graphs will be isomorphic. Boards with 2 to 12 nodes are supported (corresponding to `1 <= id < 2^66`).

```
Board(edges::Vector{Vector{Int}})
```

Construct a board graph from a specified list of outgoing edges from each node. Note, if this does not describe an undirected graph, things will go bad if it is used to construct a game graph.
