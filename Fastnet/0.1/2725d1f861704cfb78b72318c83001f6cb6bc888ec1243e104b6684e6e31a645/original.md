```
listnodes(FastNet)    
listnodes(FastNet,state)
```

Return a vector of the IDs of all nodes in FastNet *net* or all nodes in state *state* in *net*.

The one-argument method of this function returns a Vector containing the IDs of all nodes that  are in the network. The two-argument method creates a vector of all nodes in state *state*.  

See also [listneighbors](#Fastnet.listneighbors) 

# Example

```jldoctest
julia> using Fastnet

julia> net=FastNet(10,10,2,[])
Network of 0 nodes and 0 links

julia> makenodes!(net,3,1)

julia> makenodes!(net,2,2)

julia> listnodes(net)
5-element Vector{Int64}:
 1
 2
 3
 4
 5

julia> listnodes(net,2)
2-element Vector{Int64}:
 4
 5
```
