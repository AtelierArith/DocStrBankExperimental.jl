```
descendencematrix(net::HybridNetwork; checkpreorder::Bool=true)
```

Descendence matrix between all the nodes of a network: object `D` of type [`MatrixTopologicalOrder`](@ref) in which `D[i,j]` is the proportion of genetic material in node `i` that can be traced back to node `j`. If `D[i,j]>0` then `j` is a descendent of `i` (and `j` is an ancestor of `i`). The network is assumed to be pre-ordered if `checkpreorder` is false. If `checkpreorder` is true (default), `preorder!` is run on the network beforehand.
