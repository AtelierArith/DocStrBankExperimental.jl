```
countlinks(net)
countlinks(net,s)
countlinks_f(net)
countlinks_f(net,s)
```

Count the links in state *s*, or, if no state is provided, in the entire network.  

Instead of the state *s* also an Array or Tuple of states can be passed.  In this case the total number of nodes in all of the listed states is returned. 

The links in a sincle class or the entire network are counted in constant time.  For the tuples or array arguments the performance scales with the number of elements in the  Tulps/Array.  The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

If performance is critical use this function rather than linkcounts.

See also [linkcounts](#Fastnet.linkcounts)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[LinkType(1,2,1),LinkType(2,2,2)])
Network of 0 nodes and 0 links

julia> makenodes!(net,20,1)

julia> makenodes!(net,20,2)

julia> for i=1:20
         from=node(net,1,i)
         to=node(net,2,i)
         makelink!(net,from,to)
       end

julia> makelink!(net,node(net,2,1),node(net,2,2));

julia> countlinks(net)
21

julia> countlinks(net,1)
20

julia> countlinks(net,2)
1

julia> countlinks(net,[1,2])
21
```
