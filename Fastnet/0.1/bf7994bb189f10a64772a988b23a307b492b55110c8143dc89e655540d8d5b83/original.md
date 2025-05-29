```
firstlinkout(net,nid)
firstlinkout_f(net,nid)
```

Return the link id of the first outgoing link from the node with id *nid* in network *net*.  

If there are no outgoing links then the return value is 0

All versions of this function run in constant time.  The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

See also [firstlinkout](#Fastnet.firstlinkin), [nextlinkin](#Fastnet.nextlinkout) 

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> l1=makelink!(net,n1,n2);

julia> firstlink=firstlinkout(net,n1);

julia> firstlink==l1
true

julia> linksrc(net,firstlink)==n1
true

julia> linkdst(net,firstlink)==n2
true
```
