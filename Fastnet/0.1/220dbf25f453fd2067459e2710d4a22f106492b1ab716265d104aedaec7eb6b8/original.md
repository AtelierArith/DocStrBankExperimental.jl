```
degreedist(net::FastNet)
```

Return a vector of Float64 that specifies the networks degree distribution. 

The element k of the returned vector is the probability that the probability that the a randomly drawn node from the  network has degree k. 

If the elements of the vector do not add up to 1.0, the remainder is the probability that a randomly drawn node has  degree zero.  

# Example

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> makenodes!(net,4,1)

julia> makelink!(net,node(net,1),node(net,2));

julia> makelink!(net,node(net,2),node(net,3));

julia> degreedist(net)
2-element Vector{Float64}:
 0.5
 0.25
```
