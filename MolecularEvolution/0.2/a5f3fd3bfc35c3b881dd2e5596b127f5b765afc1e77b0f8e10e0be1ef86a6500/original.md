```
felsenstein_roundtrip!(tree::FelNode, models; partition_list = 1:length(tree.message), temp_message = copy_message(tree.message[partition_list]))
```

Should usually be called on the root of the tree. First propagates Felsenstein pass up from the tips to the root, then propagates Felsenstein pass down from the root to the tips, with the direction of time reversed (i.e. forward! = backward!). **This is useful when searching for the optimal root** (see [`root_optim!`](@ref)). models can either be a single model (if the messages on the tree contain just one Partition) or an array of models, if the messages have >1 Partition, or  a function that takes a node, and returns a Vector{<:BranchModel} if you need the models to vary from one branch to another. partition_list (eg. 1:3 or [1,3,5]) lets you choose which partitions to run over.
