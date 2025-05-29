```
GNNGraph(data; [graph_type, ndata, edata, gdata, num_nodes, graph_indicator, dir])
GNNGraph(g::GNNGraph; [ndata, edata, gdata])
```

A type representing a graph structure that also stores feature arrays associated to nodes, edges, and the graph itself.

The feature arrays are stored in the fields `ndata`, `edata`, and `gdata` as [`DataStore`](@ref) objects offering a convenient dictionary-like  and namedtuple-like interface. The features can be passed at construction time or added later.

A `GNNGraph` can be constructed out of different `data` objects expressing the connections inside the graph. The internal representation type is determined by `graph_type`.

When constructed from another `GNNGraph`, the internal graph representation is preserved and shared. The node/edge/graph features are retained as well, unless explicitely set by the keyword arguments `ndata`, `edata`, and `gdata`.

A `GNNGraph` can also represent multiple graphs batched togheter (see [`MLUtils.batch`](@ref) or [`SparseArrays.blockdiag`](@ref)). The field `g.graph_indicator` contains the graph membership of each node.

`GNNGraph`s are always directed graphs, therefore each edge is defined by a source node and a target node (see [`edge_index`](@ref)). Self loops (edges connecting a node to itself) and multiple edges (more than one edge between the same pair of nodes) are supported.

A `GNNGraph` is a Graphs.jl's `AbstractGraph`, therefore it supports most functionality from that library.

# Arguments

  * `data`: Some data representing the graph topology. Possible type are

      * An adjacency matrix
      * An adjacency list.
      * A tuple containing the source and target vectors (COO representation)
      * A Graphs.jl' graph.
  * `graph_type`: A keyword argument that specifies               the underlying representation used by the GNNGraph.               Currently supported values are

      * `:coo`. Graph represented as a tuple `(source, target)`, such that the `k`-th edge         connects the node `source[k]` to node `target[k]`.         Optionally, also edge weights can be given: `(source, target, weights)`.
      * `:sparse`. A sparse adjacency matrix representation.
      * `:dense`. A dense adjacency matrix representation.

    Defaults to `:coo`, currently the most supported type.
  * `dir`: The assumed edge direction when given adjacency matrix or adjacency list input data `g`.       Possible values are `:out` and `:in`. Default `:out`.
  * `num_nodes`: The number of nodes. If not specified, inferred from `g`. Default `nothing`.
  * `graph_indicator`: For batched graphs, a vector containing the graph assignment of each node. Default `nothing`.
  * `ndata`: Node features. An array or named tuple of arrays whose last dimension has size `num_nodes`.
  * `edata`: Edge features. An array or named tuple of arrays whose last dimension has size `num_edges`.
  * `gdata`: Graph features. An array or named tuple of arrays whose last dimension has size `num_graphs`.

# Examples

```julia
using GNNGraphs

# Construct from adjacency list representation
data = [[2,3], [1,4,5], [1], [2,5], [2,4]]
g = GNNGraph(data)

# Number of nodes, edges, and batched graphs
g.num_nodes  # 5
g.num_edges  # 10
g.num_graphs # 1

# Same graph in COO representation
s = [1,1,2,2,2,3,4,4,5,5]
t = [2,3,1,4,5,3,2,5,2,4]
g = GNNGraph(s, t)

# From a Graphs' graph
g = GNNGraph(erdos_renyi(100, 20))

# Add 2 node feature arrays at creation time
g = GNNGraph(g, ndata = (x=rand(100, g.num_nodes), y=rand(g.num_nodes)))

# Add 1 edge feature array, after the graph creation
g.edata.z = rand(16, g.num_edges)

# Add node features and edge features with default names `x` and `e`
g = GNNGraph(g, ndata = rand(100, g.num_nodes), edata = rand(16, g.num_edges))

g.ndata.x # or just g.x
g.edata.e # or just g.e

# Collect edges' source and target nodes.
# Both source and target are vectors of length num_edges
source, target = edge_index(g)
```

A `GNNGraph` can be sent to the GPU, for example by using Flux.jl's `gpu` function or MLDataDevices.jl's utilities. 
