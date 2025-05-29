```
linkexists(net,kid)
linkexists_f(net,kid)
```

Return true node with id *kid* exists in *net*, false otherwise.  

This function runs in constant time.  The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

See also [makelink!](#Fastnet.makelink!) 

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> linkexists(net,7)
false

julia> k=makelink!(net,n1,n2);

julia> linkexists(net,k)
true
```
