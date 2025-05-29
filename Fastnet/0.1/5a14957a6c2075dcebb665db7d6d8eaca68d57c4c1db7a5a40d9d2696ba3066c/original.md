```
nodestate(net,nid)
nodestate_f(net,nid)
```

Return the state of the node with id *nid* in network *net*. 

All version of this function run in constant time, but fast (_f) verions sacrifice some safty  checks for better performance. See [basic concepts](concepts.md) for details. 

See also [nodestate!](#Fastnet.nodestate!)

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
