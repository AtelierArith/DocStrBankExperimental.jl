```
min_vertex_cover(num_nodes::Int, edges::Vector{Tuple{Int, Int}}; num_layers::Int=1, driver=X)
```

Wrapper function setting up a problem instance for the minimum vertex cover of the graph `graph`.

### Input

  * `graph::PyObject`: The input graph, must be a [Python NetworkX](https://networkx.org/) graph.
  * `num_layers::Int=1` (optional): The number of QAOA layers usually denoted by $p$.
  * `driver=X` (optional): The driver or mixer used in the QAOA.

### Output

  * An instance of the `Problem` struct holding all relevant quantities.

### Notes

The cost function for the minimum-vertex-cover problem is 

$\hat C = -\frac{3}{4} \sum_{(i, j) \in E(G)} (\hat Z_i \hat Z_j  +  \hat Z_i  +  \hat Z_j)  + \sum_{i \in V(G)} \hat Z_i,$

where $E(G)$ is the set of edges and $V(G)$ is the set of vertices of `graph` (we have a global minus sign since we *maximize* the cost function).
