```
species(N::AbstractUnipartiteNetwork; dims::Int64=1)
```

Returns an array of species on either side of a unipartite network. In a unipartite network, species are the same on either size. This function is nevertheless useful when you want to write code that takes either side of the network in a general way.
