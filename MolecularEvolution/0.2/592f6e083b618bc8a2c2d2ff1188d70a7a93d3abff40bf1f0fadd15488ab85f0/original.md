```
felsenstein!(node::FelNode, models; partition_list = nothing)
```

Should usually be called on the root of the tree. Propagates Felsenstein pass up from the tips to the root. models can either be a single model (if the messages on the tree contain just one Partition) or an array of models, if the messages have >1 Partition, or  a function that takes a node, and returns a Vector{<:BranchModel} if you need the models to vary from one branch to another. partition_list (eg. 1:3 or [1,3,5]) lets you choose which partitions to run over.
