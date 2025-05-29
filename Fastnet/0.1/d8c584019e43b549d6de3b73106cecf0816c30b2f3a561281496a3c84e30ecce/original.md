```
listnodestates(net)
```

Return an array that contains the ids and states of all nodes in *net*. 

The return value will be a two-dimensional array of dimension (K,2), where  K is the number of nodes in the network. Each row corresponds to one node.  The contests of the array ar

  * First Column: ID of the respective node
  * Second column: State of the node

Warning: Do not rely on the row index to be identical to the node ID

See also [listlinks](#Fastnet.listlinks) 

# Example

```jldoctest
julia> using Fastnet

julia> net=FastNet(100,100,3,[])
Network of 0 nodes and 0 links

julia> makenodes!(net,2,1)

julia> makenodes!(net,2,2)

julia> makenodes!(net,3,3)

julia> listnodestates(net)
7×2 Matrix{Int64}:
 1  1
 2  1
 3  2
 4  2
 5  3
 6  3
 7  3
```
