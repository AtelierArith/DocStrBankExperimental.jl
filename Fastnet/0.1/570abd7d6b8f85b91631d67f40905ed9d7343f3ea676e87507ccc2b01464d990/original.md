```
configmodel!(net::FastNet,degreedist;<keyword arguments>)
```

Create a configuration model style network with prescribed degree distribution, *degreedist*.

The network in *net* is replaced with the new topology. The degree distribution is specified in   terms of a vector of Float64 variables such that *degreedist[k]* is specifies, p<sub>k</sub>, the probability that a randomly drawn node has degree k. If the elements of *degreedist* add up to less than 1.0 the  remaining nodes will have degree zero.   

The network generation is fast and unbiased but isn't guaranteed to result in a simple graph.  The algorithm will try to match the desired degree distribution as closely as possible, but small discrepancies can appear if the degree distribution would result in an odd degree sum  or non integer numbers of nodes of certain degrees. 

If there FastNet is not large enough to accomodate the desired number of links or nodes an argument error  will be thrown. 

The keyword arguments are 

  * N : The number of nodes that will be used in the creation of the network
  * S : The state of the nodes. All nodes will be set to this state.

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> configmodel!(net,[0.5,0.25,0.25],N=200)
Network of 200 nodes and 175 links

julia> degreedist(net)
3-element Vector{Float64}:
 0.5
 0.25
 0.25

julia> configmodel!(net,[0.5,0.25],N=200)
Network of 200 nodes and 100 links

julia> degreedist(net)
2-element Vector{Float64}:
 0.5
 0.25
```
