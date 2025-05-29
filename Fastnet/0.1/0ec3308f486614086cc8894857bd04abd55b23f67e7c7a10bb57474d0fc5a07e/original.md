```
showlinks(net)
```

Print information on all links in FastNet *net*.

This function is mainly intended for testing/debugging. Use it only for networks with few links.

See also [shownodes](#Fastnet.shownodes)

# Examples

```jldoctest julia> using Fastnet

julia> net=FastNet(1000,2000,2,[LinkType(1,1),LinkType(1,2),LinkType(2,2)]);

julia> makenodes!(net,5,1)

julia> makenodes!(net,5,2)

julia> makelink!(net,node(net,1,1),node(net,1,2)); 1

julia> makelink!(net,node(net,1,1),node(net,2,1)) 2

julia> makelink!(net,node(net,2,1),node(net,2,2)) 3

julia> makelink!(net,node(net,2,2),node(net,1,2)) 4

julia> showlinks(net) id      src     dest    state 1       1       2       1 2       1       6       2 3       6       7       3 4       7       2       2 
