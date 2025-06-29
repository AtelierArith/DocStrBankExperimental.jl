```
randomgraph!(net;<keyword arguments>)
```

Create an ER random graph in the network *net*. 

The network isn't guaranteed to be a simple graph, but in large sparse  networks it is simple with high probability. 

By default all nodes and links that the network can accommodate will be used and  all nodes will be set to state one. This behavior can be controlled by the following  keyword arguments:

  * N : The number of nodes that will be used in the creation of the random graph. All other nodes will be removed from the network.
  * K : The number of links that will be used in the creation of the random graph. All other links will be removed from the network.
  * S : The state of the nodes. All nodes will be set to this state.

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,1,[])
Network of 0 nodes and 0 links

julia> randomgraph!(net)
Network of 1000 nodes and 2000 links

julia> nullgraph!(net)
Network of 0 nodes and 0 links

julia> randomgraph!(net,N=100,K=10)
Network of 100 nodes and 10 links
```
