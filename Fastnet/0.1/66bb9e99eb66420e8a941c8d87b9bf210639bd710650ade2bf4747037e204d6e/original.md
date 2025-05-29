link(net,rp) link(net,s,rp) link*f(net,rp) link*f(net,s,rp)

Determine link id from relative *rp*  position and node state *s*.

The link function provides a way to access links form the set of nodes in a certain link state, or from the set of all links. The two-argument version returns the id of the  link at poition *rp* in network *net*. The three-argument version returns the id of the link at  poition *rp* within the set of links that are in state *s*.

All version of this function run in constant time, but fast (_f) verions sacrifice some safty  checks for better performance. See [basic concepts](concepts.md) for details. 

See also [adjacent](#Fastnet.adjacent)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[LinkType(1,2),LinkType(1,1),LinkType(2,2)])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> n3=makenode!(net,2);

julia> makelink!(net,n1,n2);

julia> makelink!(net,n2,n3);

julia> makelink!(net,n3,n1);

julia> lid=link(net,2,1);

julia> linkdst(net,lid)==n2
true

julia> linksrc(net,lid)==n1
true
```
