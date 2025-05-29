```
listlinks(net)
```

Return an array that contains the source and destination of all links in *net*. 

The return value will be a two-dimensional array of dimensions (K,3), where  K is the number of links in the network. Each row corresponds to one link.  The contests of the array are

  * First column: Identical to the linkid of the respective link
  * Second column: Source node of the link
  * Third column: Destination node of the link

Warning: Do not rely on the row index to be identical to the link ID

See also [savelinklist](#Fastnet.savelinklist) 

# Example

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> makenodes!(net,5,1)

julia> makelink!(net,1,2)
1

julia> makelink!(net,1,3)
2

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> makenodes!(net,5,1)

julia> makelink!(net,1,2)
1

julia> makelink!(net,2,3)
2

julia> makelink!(net,3,4)
3

julia> makelink!(net,4,5)
4

julia> makelink!(net,5,1)
5

julia> listlinks(net)
5×3 Matrix{Int64}:
 1  1  2
 2  2  3
 3  3  4
 4  4  5
 5  5  1
```
