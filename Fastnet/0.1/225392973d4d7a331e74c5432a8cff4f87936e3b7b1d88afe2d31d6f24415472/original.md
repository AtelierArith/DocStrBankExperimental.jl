```
makenode!(net,s)
makenode_f!(net,s)
```

Create a new node in state *s* in the network *net* and return it's id. 

Worst-case performance of both versions of this function scales only with the number of node states.  

The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

See also [destroynode!](#Fastnet.destroynode!), [makenodes!](#Fastnet.makenodes!)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> makenode!(net,2)
1

julia> net
Network of 1 nodes and 0 links

julia> nodestate(net,1)
2
```
