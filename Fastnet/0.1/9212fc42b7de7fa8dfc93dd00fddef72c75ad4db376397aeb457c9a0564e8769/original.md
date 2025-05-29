```
nodeexists(net,nid)
nodeexists_f(net,nid)
```

Return if a node with id *nid* exists in *net*, false otherwise.  

This function runs in constant time.  The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

See also [makenode!](#Fastnet.makenode!), [destroynode!](#Fastnet.destroynode!) 

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> nodeexists(net,n1)
true
```
