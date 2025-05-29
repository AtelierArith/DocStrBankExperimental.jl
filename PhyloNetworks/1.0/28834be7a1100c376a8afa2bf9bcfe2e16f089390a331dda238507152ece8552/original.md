```
cladewiseorder!(net::HybridNetwork)
```

Update the internal attribute `net.vec_int1`. Used for plotting the network. In the major tree, all nodes in a given clade are consecutive. On a tree, this function also provides a pre-ordering of the nodes. The edges' direction needs to be correct before calling [`cladewiseorder!`](@ref), using [`directedges!`](@ref)
