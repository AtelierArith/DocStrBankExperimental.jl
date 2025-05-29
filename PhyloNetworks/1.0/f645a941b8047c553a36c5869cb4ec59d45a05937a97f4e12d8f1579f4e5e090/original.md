```
nameinternalnodes!(net::HybridNetwork, prefix="i")
```

Add names to nodes in `net` that don't already have a name. Leaves already have names; but if not, they will be given names as well. New node names will be of the form "prefixk" where `k` is an integer. So by default, new node names will be of the form "i1", "i2", etc.

# examples

```jldoctest
julia> net = readnewick("((a:1,(b:1)#H1:1::0.8):5,(#H1:0::0.2,c:1):1);");

julia> nameinternalnodes!(net, "I") # by default, shown without internal node names
HybridNetwork, Rooted Network
7 edges
7 nodes: 3 tips, 1 hybrid nodes, 3 internal tree nodes.
tip labels: a, b, c
((a:1.0,(b:1.0)#H1:1.0::0.8)I1:5.0,(#H1:0.0::0.2,c:1.0)I2:1.0)I3;

julia> writenewick(net; internallabel=false) # by default, writenewick shows internal names if they exist
"((a:1.0,(b:1.0)#H1:1.0::0.8):5.0,(#H1:0.0::0.2,c:1.0):1.0);"

julia> net = readnewick("((int5:1,(b:1)#H1:1::0.8):5,(#H1:0::0.2,c:1):1);"); # one taxon name starts with "int"

julia> nameinternalnodes!(net, "int");

julia> writenewick(net)
"((int5:1.0,(b:1.0)#H1:1.0::0.8)int6:5.0,(#H1:0.0::0.2,c:1.0)int7:1.0)int8;"
```
