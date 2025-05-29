```
nodecounts(net)
nodecounts_f(net)
```

Return an Array containing the number of nodes in the vairous node states. 

The time required for this function scales only with the number of node states (it is independent of the number of nodes). 

The alternative (_f) version of this function is identical to nodecounts and is provided only for convenience. 

See also [countnodes](#Fastnet.countnodes)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> randomgraph!(net)
Network of 1000 nodes and 2000 links

julia> for i=1:20
         n=node(net,1,1)
         nodestate!(net,n,2)
       end

julia> nodecounts(net)
2-element Vector{Int64}:
 980
  20
```
