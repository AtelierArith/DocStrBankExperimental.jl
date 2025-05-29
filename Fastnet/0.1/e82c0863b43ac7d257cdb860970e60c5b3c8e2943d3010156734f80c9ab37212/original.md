```
randomnode(net)
randomnode(net,s)
randomnode_f(net)
randomnode_f(net,s)
```

Return the id of a random node drawn from *net*.

If the second argument *s* is not provided the node will be drawn uniformly from  all nodes in the network. If *s* is an integer then the node will be drawn uniformly  from the nodes in state *s*. If *s* is an Array or Tuple of Ints then the node will be  drawn uniformly from the nodes in the states listed. 

This function runs in constant time if *s* is integer or omitted. If *s* is an Array or Tuple the  worst case performance scales only with the number of node states.   The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

The safe versions of this function will throw an ArgumentError with an informative error message when trying to pick a node from an empty set. With the fast (_f) version, trying to pick a node from  an empty set will also result in an ArgumentError being thrown, but in this case the message will be  something like "Range must be non-empty".  

See also [node](#Fastnet.node)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> makenodes!(net,100,1);

julia> makenodes!(net,100,2);

julia> nodestate(net,randomnode(net,1))
1
julia> nodestate(net,randomnode(net,2))
2
```
