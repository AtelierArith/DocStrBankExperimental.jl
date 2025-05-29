```
NNI!(root::T, target::Int64)::Int64  where T<:AbstractNode
```

This function does a nearest neighbour interchange (NNI) move on the tree specified by `root`. The target is identified by the number of the target node. The function returns 1 if the move was successfull and 0 else.
