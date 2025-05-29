```
nodestate!(net,nid,s)
nodestate_f!(net,nid,s)
```

Set the node with id *nid* in net *net* to *s*.

Worst-case performance of both versions of this function is O(ks*k)+O(ns) where ks is the number of  tracked link states, k is the degree of the affected node and ns is the number of node states.  

The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

See also [nodestate](#Fastnet.nodestate)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> randomgraph!(net)
Network of 1000 nodes and 2000 links

julia> nodestate(net,1)
1

julia> nodestate!(net,1,2)

julia> nodestate(net,1)
2
```
