```
makenodes!(net,N,s)
makenodes_f!(net,N,s)
```

Create *N* nodes in state *s* in the network *net.  

Worst case performance of this function scales only with the number of node states.  The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

See also [makenode!](#Fastnet.makenode!), [destroynode!](#Fastnet.destroynode!) 

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> makenodes!(net,100,1);

julia> net
Network of 100 nodes and 0 links
```
