```
FastNet(n,k,c,tlist;<keyword arguments>)
```

Create a FastNet object that represents a network structe.

Memory will be allocated for up to *n* nodes, up to *k* links. Nodes can be in one of *c* different states.

The argument tlist is an array or tuple of LinkType. This list tells the networks which types of links are  important for you. For example in an epidemic simulation the we are particularly interested in links between  infected and susceptible nodes. FastNet will do the necessary bookkeeping, to enable very fast counting, selection, etc. of the links that are in a state listed in tlist. 

Note that the order of elements of tlist is not arbitrary. FastNet will think of links that match the first element  of tlist as being in link state 1. The links that match the sceond type in link state 2, and so on. 

WARNING: Each link in the network can only be in any one state at any time passing a tlist that contains overlapping  link types (e.g. [LinkType([1,2],3),LinkType(3,1)] )  will result in an ArgumentError being thrown. 

FastNet supports a number of optional keyword arguments:

  * nodealias : a vector of strings that will be used as names of node states in outputs
  * linkalias : a vector of strings that will be used as names of link states in outputs
  * rng : specifies a custom random number generator

The network will initially be empty (i.e. a null graph)

# Examples

```jldoctest
julia> using Fastnet

julia> FastNet(10,9,1,[])
Network of 0 nodes and 0 links

julia> FastNet(100,1000,3,[LinkType(1,2),LinkType(3,"*",1)])
Network of 0 nodes and 0 links

julia> using Random

julia> mt = MersenneTwister(1234);

julia> const S=1;

julia> const I=2;

julia> SI_link=LinkType(S,I)
Links of the form:  (1) --- (2)

julia> net=FastNet(10000,60000,2,[SI_link],nodealias=["S","I"],linkalias=["S-I"],rng=mt)
Network of 0 nodes and 0 links
```
