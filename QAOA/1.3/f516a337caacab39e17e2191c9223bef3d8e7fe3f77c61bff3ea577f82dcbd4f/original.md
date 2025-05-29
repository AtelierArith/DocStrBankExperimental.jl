```
max_cut(num_nodes::Int, edges::Vector{Tuple{Int, Int}}; num_layers::Int=1, driver=X)
```

Wrapper function setting up an instance of the MaxCut problem for the graph `graph`.

### Input

  * `graph::PyObject`: The input graph, must be a [Python NetworkX](https://networkx.org/) graph.
  * `num_layers::Int=1` (optional): The number of QAOA layers usually denoted by $p$.
  * `driver=X` (optional): The driver or mixer used in the QAOA.

### Output

  * An instance of the `Problem` struct holding all relevant quantities.

### Notes

The cost function for the MaxCut problem as defined in the [original QAOA paper](https://arxiv.org/abs/1411.4028) is

$\hat C = -\frac{1}{2} \sum_{(i, j) \in E(G)} \hat Z_i \hat Z_j + \mathrm{const.},$

where $E(G)$ is the set of edges of the graph $G$.
