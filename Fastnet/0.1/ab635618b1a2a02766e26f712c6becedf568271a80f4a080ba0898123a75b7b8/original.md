```
linkdst!(net,kid)
linkdst_f!(net,kid)
```

Return the id of the node at the destination of link *kid* in *net*. 

All versions of this function run in constant time.  The fast (_f) verion sacrifices some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

See also [makelink!](#Fastnet.makelink!)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,2);

julia> k1=makelink!(net,n1,n2);

julia> linkdst(net,k1)==n2
true
```
