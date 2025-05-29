```
randomlink(net)
randomlink(net,s)
randomlink_f(net)
randomlink_f(net,s)
```

Return the id of a random link drawn from *net*.

If the second argument *s* is not provided the link will be drawn uniformly from  all links in the network. If *s* is an integer then the link will be drawn uniformly  from the links in state *s*. If *s* is an Array or Tuple of Ints then the link will be  drawn uniformly from the links in the states listed. 

This function runs in constant time if *s* is integer or omitted. If *s* is an Array or Tuple the  worst case performance scales only with the number of tracked link states.   The fast (_f) verions sacrifice some safty checks for better performance.  See [basic concepts](concepts.md) for details. 

The safe versions of this function will throw an ArgumentError with an informative error message when trying to pick a link from an empty set. With the fast (_f) version, trying to pick a link from  an empty set will also result in an ArgumentError being thrown, but in this case the message will be  something like "Range must be non-empty".  

See also [link](#Fastnet.link)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[LinkType(2,2,2)])
Network of 0 nodes and 0 links

julia> randomgraph!(net);

julia> for i=1:500
         nd=randomnode(net,1)
         nodestate!(net,nd,2)
       end

julia> lnk=randomlink(net,1);

julia> linkstate(net,lnk)
1
```
