```
sharedpathmatrix(net::HybridNetwork; checkpreorder::Bool=true)
```

This function computes the shared path matrix between all the nodes of a network. It assumes that the network is in the pre-order. If checkpreorder is true (default), then it runs function `preorder!` on the network beforehand.

Returns an object of type [`MatrixTopologicalOrder`](@ref).
