```
countnodes(net)
countnodes(net,s)
countnodes_f(net)
countnodes_f(net,s)
```

Count the nodes in state *s*, or, if no state is provided, in the entire network.  

Instead of the state *s* also an Array or Tuple of states can be passed.  In this case the total number of nodes in all of the listed states is returned. 

All versions of this function run in constant time.  The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

If performance is critical use this function rather than nodecounts.

See also [nodecounts](#Fastnet.nodecounts)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> for i=1:20
         makenode!(net,1)
         end

julia> for i=1:10
         makenode!(net,2)
         end

julia> countnodes(net)
30

julia> countnodes(net,1)
20

julia> countnodes(net,(1,2))
30
```
