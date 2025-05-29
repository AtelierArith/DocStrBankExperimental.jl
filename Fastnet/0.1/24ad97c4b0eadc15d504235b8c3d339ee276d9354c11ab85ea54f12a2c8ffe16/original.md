```
node(net,rp)
node(net,s,rp)
node_f(net,rp)
node_f(net,s,rp)
```

Determine node id from relative position and node state.

The node function provides a way to access nodes form a the set of nodes in certain states, or from the set of all nodes in a simple way. The two-argument version returns the id of the  node at poition *rp* in network *net*. The three-argument version returns the id of the node at  poition *rp* within all nodes in state *s*.

All version of this function run in constant time, but fast (_f) verions sacrifice some safty  checks for better performance. See [basic concepts](concepts.md) for details. 

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> randomgraph!(net)
Network of 1000 nodes and 2000 links

julia> nodestate!(net,123,2)

julia> nodestate!(net,345,2)

julia> node(net,2,1)
345

julia> node(net,2,2)
123

julia> node(net,1)
1

julia> destroynode!(net,1)

julia> node(net,1)
998
```
