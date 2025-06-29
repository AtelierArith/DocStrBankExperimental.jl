```
GlobalPool(aggr)
```

Global pooling layer for graph neural networks. Takes a graph and feature nodes as inputs and performs the operation

$$
\mathbf{u}_V = \square_{i \in V} \mathbf{x}_i
$$

where $V$ is the set of nodes of the input graph and  the type of aggregation represented by $\square$ is selected by the `aggr` argument.  Commonly used aggregations are `mean`, `max`, and `+`.

See also [`reduce_nodes`](@ref).

# Examples

```julia
using Flux, GraphNeuralNetworks, Graphs

pool = GlobalPool(mean)

g = GNNGraph(erdos_renyi(10, 4))
X = rand(32, 10)
pool(g, X) # => 32x1 matrix


g = Flux.batch([GNNGraph(erdos_renyi(10, 4)) for _ in 1:5])
X = rand(32, 50)
pool(g, X) # => 32x5 matrix
```
