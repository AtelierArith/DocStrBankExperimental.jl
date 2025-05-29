```
indegree(net,nid)
indegree_f(net,nid)
```

Return the incoming degree of the node with id *nid* in network *net*.  

The worst case performance scales only with the indegree of the affected node.  The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

See also [degree](#Fastnet.degree), [outdegree](#Fastnet.outdegree) 

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> n3=makenode!(net,1);

julia> makelink!(net,n1,n2);

julia> makelink!(net,n3,n2);

julia> indegree(net,n1)
0

julia> indegree(net,n2)
2
```
