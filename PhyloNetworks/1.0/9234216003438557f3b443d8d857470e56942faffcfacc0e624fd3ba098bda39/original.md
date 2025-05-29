```
removedegree2nodes!(net::HybridNetwork, keeproot::Bool=false)
```

Delete *all* nodes of degree two in `net`, fusing the two adjacent edges together each time, and return the network. If the network has a degree-2 root and `keeproot` is false, then the root is eliminated as well, leaving the network unrooted. The only exception to this rule is if the root is incident to 2 (outgoing) hybrid edges. Removing the root should leave a loop-edge (equal end point), which we don't want to do, to preserve the paths in the original network. In this case, the root is maintained even if `keeproot` is false. If `keeproot` is true, then the root is kept even if it's of degree 2.

See [`fuseedgesat!`](@ref).

```jldoctest
julia> net = readnewick("(((((S1,(S2)#H1),(#H1,S3)))#H2),(#H2,S4));");

julia> PhyloNetworks.breakedge!(net.edge[3], net); # create a degree-2 node along hybrid edge

julia> PhyloNetworks.breakedge!(net.edge[3], net); # another one: 2 in a row

julia> PhyloNetworks.breakedge!(net.edge[10], net); # another one, elsewhere

julia> writenewick(net) # extra pairs of parentheses
"((#H2,S4),(((((S1,(((S2)#H1))),(#H1,S3)))#H2)));"

julia> removedegree2nodes!(net);

julia> writenewick(net) # even the root is gone
"(#H2,S4,(((S1,(S2)#H1),(#H1,S3)))#H2);"

julia> net = readnewick("((((C:0.9)I1:0.1)I3:0.1,((A:1.0)I2:0.4)I3:0.6):1.4,(((B:0.2)H1:0.6)I2:0.5)I3:2.1);");

julia> removedegree2nodes!(net, true);

julia> writenewick(net, round=true) # the root was kept
"((C:1.1,A:2.0):1.4,B:3.4);"

```
