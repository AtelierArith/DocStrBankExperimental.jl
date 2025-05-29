```
listneighbors(FastNet,nid)
```

Return a vector of the IDs of all nodes that are asjacent to node *nid* in FastNet *net*. 

This function is comparatively slow as it needs to allocate the vector. In your *rates!*  and process functions it is preferable to iterate over the neighbors using firstlinkout, firstlinkin, nexlinkout, nextlinkin. 

See also [listnodes](#Fastnet.listnodes) 

# Example

```jldoctest
julia> using Fastnet

julia> net=FastNet(10,10,2,[])
Network of 0 nodes and 0 links

julia> makenodes!(net,3,1)

julia> makenodes!(net,2,2)

julia> listnodes(net)
5-element Vector{Int64}:
 1
 2
 3
 4
 5

 julia> listnodes(net,2)
 2-element Vector{Int64}:
 4
 5 
```
