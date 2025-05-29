```
destroylink!(net,kid)
destroylink_f!(net,kid)
```

Destroy the link with id *kid* in network *net*. 

All versions of this function run in constant time.  The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

See also [makelink!](#Fastnet.makelink!)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,2);

julia> makelink!(net,n1,n2);

julia> net
Network of 2 nodes and 1 links

julia> lnk=randomlink(net);

julia> destroylink!(net,lnk)

julia> net
Network of 2 nodes and 0 links
```
