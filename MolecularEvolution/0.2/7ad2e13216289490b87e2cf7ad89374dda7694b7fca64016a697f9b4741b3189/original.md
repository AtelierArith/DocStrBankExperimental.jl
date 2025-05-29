```
root_optim!(tree::FelNode, models; <keyword arguments>)
```

Optimizes the root position and root state of a tree. Returns the new, optimal root node. models can either be a single model (if the messages on the tree contain just one Partition) or an array of models, if the messages have >1 Partition, or  a function that takes a node, and returns a Vector{<:BranchModel} if you need the models to vary from one branch to another.

# Keyword Arguments

  * `partition_list=1:length(tree.message)`: (eg. 1:3 or [1,3,5]) lets you choose which partitions to run over (but you probably want to optimize root position and root state with all models, the default option).
  * `root_LL!=default_root_LL_wrapper(tree.parent_message[partition_list])`: a function that takes a message and returns a (optimal) parent message and LL (log likelihood). The default option uses the constant `tree.parent_message[partition_list]` as parent message for all root-candidates.
  * `K=10`: the number of equidistant root-candidate points along a branch. (only to be used in the frequentist framework!?)
