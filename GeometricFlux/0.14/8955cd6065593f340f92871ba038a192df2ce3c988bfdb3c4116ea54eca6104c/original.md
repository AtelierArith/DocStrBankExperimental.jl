```
node2vec(g; walks_per_node, len, p, q, dims)
```

Returns an embedding matrix with size of (`nv(g)`, `dims`). It computes node embeddings on graph `g`. It performs biased random walks on the graph, then computes word embeddings by treating those random walks as sentences.

# Arguments

  * `g::FeaturedGraph`: The graph to perform random walk on.
  * `walks_per_node::Int`: Number of walks starting on each node, total number of walks is `nv(g) * walks_per_node`
  * `len::Int`: Length of random walks
  * `p::Real`: Return parameter. It controls the likelihood of immediately revisiting a node in the walk
  * `q::Real`: In-out parameter. It allows the search to differentiate between inward and outward nodes.
  * `dims::Int`: Number of vector dimensions
