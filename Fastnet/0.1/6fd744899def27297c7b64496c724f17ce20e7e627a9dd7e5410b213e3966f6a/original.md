```
linkcounts(net)
linkcounts_f(net)
```

Return an Array containing the number of link in the vairous link states. 

The elements of the array will show the counts in the same order in which the link types  were passed to the FastNet Constructor. 

The time required for this function scales only with the number of link states (it is independent of the number of links). 

The alternative (_f) version of this function is identical only provided for convenience. 

See also [countlinks](#Fastnet.countlinks)

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

julia> linkcounts(net)
3-element Vector{Int64}:
 2
 1
 0
```
