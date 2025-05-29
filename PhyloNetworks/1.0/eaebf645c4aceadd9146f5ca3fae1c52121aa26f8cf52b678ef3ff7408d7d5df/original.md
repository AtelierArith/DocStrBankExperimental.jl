```
rotate!(net::HybridNetwork, nodeNumber::Integer; orderedEdgeNum::Array{Int,1})
```

Rotates the order of the node's children edges. Useful for plotting, to remove crossing edges. If `node` is a tree node with no polytomy, the 2 children edges are switched and the optional argument `orderedEdgeNum` is ignored.

Use `plot(net, shownodenumber=true, showedgenumber=false)` to map node and edge numbers on the network, as shown in the examples below. (see package [PhyloPlots](https://github.com/juliaphylo/PhyloPlots.jl))

Warning: assumes that edges are correctly directed (ischild1 updated). This is done by `plot(net)`. Otherwise run `directedges!(net)`.

# Example

```julia
julia> net = readnewick("(A:1.0,((B:1.1,#H1:0.2::0.2):1.2,(((C:0.52,(E:0.5)#H2:0.02::0.7):0.6,(#H2:0.01::0.3,F:0.7):0.8):0.9,(D:0.8)#H1:0.3::0.8):1.3):0.7):0.1;");
julia> using PhyloPlots
julia> plot(net, shownodenumber=true)
julia> rotate!(net, -4)
julia> plot(net)
julia> net=readnewick("(4,((1,(2)#H7:::0.864):2.069,(6,5):3.423):0.265,(3,#H7:::0.136):10.0);");
julia> plot(net, shownodenumber=true, showedgenumber=true)
julia> rotate!(net, -1, orderedEdgeNum=[1,12,9])
julia> plot(net, shownodenumber=true, showedgenumber=true)
julia> rotate!(net, -3)
julia> plot(net)
```

Note that `LinearAlgebra` also exports a function named `rotate!` in Julia v1.5. If both packages need to be used in Julia v1.5 or higher, usage of `rotate!` needs to be qualified, such as with `PhyloNetworks.rotate!`.
