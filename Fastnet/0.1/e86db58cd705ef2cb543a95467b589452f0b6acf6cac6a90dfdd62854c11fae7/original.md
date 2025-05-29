```
degree(net,nid)
degree_f(net,nid)
```

Return the degree of the node with id *nid* in network *net*.  

Here degree is interpreted as the number of times this node appears an an endpoint of a link, hence self-loops contribute 2 to the degree of the node that they link to. 

The worst case performance scales only with the degree of the affected node.  The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

See also [indegree](#Fastnet.indegree), [outdegree](#Fastnet.outdegree) 

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> n3=makenode!(net,1);

julia> makelink!(net,n1,n2);

julia> makelink!(net,n2,n3);

julia> degree(net,n1)
1

julia> degree(net,n2)
2
```
