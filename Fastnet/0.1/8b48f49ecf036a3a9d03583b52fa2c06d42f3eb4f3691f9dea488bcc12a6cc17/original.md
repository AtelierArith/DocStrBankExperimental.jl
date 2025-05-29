```
linkstate(net,kid)
linkstate_f(net,kid)
```

Return the state of the link with id *kid* in network *net*. 

Note that the link states are numbered in the order in which they were passed to  the FastNet Constructor. 

All version of this function run in constant time, but fast (_f) verion sacrifices some safty  checks for better performance. See [basic concepts](concepts.md) for details. 

See also [nodestate!](#Fastnet.nodestate!), [FastNet](#FastNet.FastNet)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[LinkType(1,2),LinkType(1,1),LinkType(2,2)])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> lnk=makelink!(net,n1,n2);

julia> linkstate(net,lnk)
2
```
