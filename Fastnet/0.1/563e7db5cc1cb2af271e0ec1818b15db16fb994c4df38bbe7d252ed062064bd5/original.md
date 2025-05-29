```
regulargraph!(net::FastNet,deg;<keyword arguments>)
```

Create a regular graph with node degree *deg*. 

The network in *net* is replaced with the new topology in which all nodes have degree *deg* and are randomly connected. If the number of nodes is not specified the function will try to use all nodes allowed by net. 

The network generation is fast and unbiased, but isn't guaranteed to result in a simple graph. 

Note that finite regular graphs with odd node degree and odd number of nodes do not exist. Hence  either *deg* or the number of nodes must be even. 

If there FastNet is not large enough to accomodate the desired number of links or nodes an argument error  will be thrown. 

The keyword arguments are 

  * N : The number of nodes that will be used in the creation of the network
  * S : The state of the nodes. All nodes will be set to this state.

# Examples

```jldoctest
julia> using Fastnet

julia>  net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> regulargraph!(net,4)
Network of 1000 nodes and 2000 links

julia> degreedist(net)
4-element Vector{Float64}:
 0.0
 0.0
 0.0
 1.0
```
