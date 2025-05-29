```
nullgraph!(net)
```

Remove all nodes and links from the network. 

The first argument *net* is a FastNet structure that is be used in the simulation. 

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,1,[])
Network of 0 nodes and 0 links

julia> randomgraph!(net)
Network of 1000 nodes and 2000 links

julia> nullgraph!(net)
Network of 0 nodes and 0 links
```
