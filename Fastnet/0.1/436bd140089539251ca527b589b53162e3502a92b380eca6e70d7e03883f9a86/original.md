```
LinkType(from,to,dir=2)
```

Create a LinkType structure that describes the properties of a type of link in the network. 

Think of a LinkType as a set of criteria that describe a certain sort of link. The first two arguments  specify the states of the nodes at the start and end of the link respectively. The third argument specified if the LinkType can either be 1 or 2, where *dir=1* signifies that the link type should be interpreted as directed (unidirectional) and *dir=2* signifies that it should be interpreted as undirected (bidirectional). 

The state of the node at the start and end of this type of link can be specified in different ways.  A value of 0 or * for *from* or *to* means that the respective node can be in any state. An integer value corresponding to a node state means that the node must be in the respective state. An Array or Tuple of Ints means that the  node must be in one of the states listed.    

# Examples

```jldoctest
julia> using Fastnet

julia> LinkType(3,4)
Links of the form:  (3) --- (4)

julia> LinkType(3,4,1)
Links of the form:  (3) --> (4)

julia> LinkType(3,4,2)
Links of the form:  (3) --- (4)

julia> LinkType("*",4)
Links of the form:  (any) --- (4)

julia> LinkType(4,0)
Links of the form:  (4) --- (any)

julia> LinkType((1,2),3)
Links of the form:  (1/2) --- (3)

julia> LinkType(4,[1,2],1)
Links of the form:  (4) --> (1/2)
```
