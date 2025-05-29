```
propagate(fmsg, g, aggr; [xi, xj, e])
propagate(fmsg, g, aggr xi, xj, e=nothing)
```

Performs message passing on graph `g`. Takes care of materializing the node features on each edge,  applying the message function `fmsg`, and returning an aggregated message $\bar{\mathbf{m}}$  (depending on the return value of `fmsg`, an array or a named tuple of  arrays with last dimension's size `g.num_nodes`).

It can be decomposed in two steps:

```julia
m = apply_edges(fmsg, g, xi, xj, e)
m̄ = aggregate_neighbors(g, aggr, m)
```

GNN layers typically call `propagate` in their forward pass, providing as input `f` a closure.  

# Arguments

  * `g`: A `GNNGraph`.
  * `xi`: An array or a named tuple containing arrays whose last dimension's size        is `g.num_nodes`. It will be appropriately materialized on the       target node of each edge (see also [`edge_index`](@ref GNNGraphs.edge_index)).
  * `xj`: As `xj`, but to be materialized on edges' sources.
  * `e`: An array or a named tuple containing arrays whose last dimension's size is `g.num_edges`.
  * `fmsg`: A generic function that will be passed over to [`apply_edges`](@ref).      Has to take as inputs the edge-materialized `xi`, `xj`, and `e`      (arrays or named tuples of arrays whose last dimension' size is the size of      a batch of edges). Its output has to be an array or a named tuple of arrays     with the same batch size. If also `layer` is passed to propagate,     the signature of `fmsg` has to be `fmsg(layer, xi, xj, e)`      instead of `fmsg(xi, xj, e)`.
  * `aggr`: Neighborhood aggregation operator. Use `+`, `mean`, `max`, or `min`.

# Examples

```julia
using GraphNeuralNetworks, Flux

struct GNNConv <: GNNLayer
    W
    b
    σ
end

Flux.@layer GNNConv

function GNNConv(ch::Pair{Int,Int}, σ=identity)
    in, out = ch
    W = Flux.glorot_uniform(out, in)
    b = zeros(Float32, out)
    GNNConv(W, b, σ)
end

function (l::GNNConv)(g::GNNGraph, x::AbstractMatrix)
    message(xi, xj, e) = l.W * xj
    m̄ = propagate(message, g, +, xj=x)
    return l.σ.(m̄ .+ l.bias)
end

l = GNNConv(10 => 20)
l(g, x)
```

See also [`apply_edges`](@ref) and [`aggregate_neighbors`](@ref).
