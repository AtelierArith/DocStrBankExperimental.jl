```
destroynode!(net,nid)
destroynode_f!(net,nid)
```

Destroy the node with id *nid* in network *net*. 

Worst-case performance of both versions of this function is O(ks*k)+O(ns) where ks is the number of  tracked link states, k is the degree of the affected node and ns is the number of node states.  

The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

See also [makenode!](#Fastnet.makenode!)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> n=makenode!(net,1);

julia> net
Network of 1 nodes and 0 links

julia> destroynode!(net,n)

julia> net
Network of 0 nodes and 0 links
```
