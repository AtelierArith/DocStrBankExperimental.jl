```
makelink!(net,src,dst)
makelink_f!(net,src,dst)
```

Create a new link from node *src* to node*dst* in the network *net* and return it's id. 

Worst-case performance of both versions of this function scales only with the number of tracked link states.  

The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

See also [destroylink!](#Fastnet.destrolink!)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> makelink!(net,n1,n2);

julia> net
Network of 2 nodes and 1 links
```
