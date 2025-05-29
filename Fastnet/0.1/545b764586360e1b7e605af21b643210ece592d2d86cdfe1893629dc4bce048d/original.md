```
nextlinkout!(net,kid)
nextlinkout_f!(net,kid)
```

Get the id of the next outgoing link from the node at the source of link *kid* in *net*. 

This function can be used to iterate over the outgoing links of a node. If *kid* is the nodes last link the return value is zero. 

All versions of this function run in constant time.  The fast (_f) verion sacrifices some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

See also [firstlinkout](#Fastnet.firstlinkout), [nextlinkin](#Fastnet.nextlinkin)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> n3=makenode!(net,1);

julia> n4=makenode!(net,1);

julia> makelink!(net,n1,n2)
1

julia> makelink!(net,n1,n3)
2

julia> makelink!(net,n1,n4)
3

julia> k=firstlinkout(net,n1);

julia> while k!=0
           println(k)
           k=nextlinkout(net,k)
           end
3
2
1
```
