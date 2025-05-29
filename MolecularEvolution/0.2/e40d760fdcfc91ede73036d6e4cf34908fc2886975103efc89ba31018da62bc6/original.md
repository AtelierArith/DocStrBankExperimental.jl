```
nni_optim!(tree::FelNode, models; <keyword arguments>)
```

Considers local branch swaps for all branches recursively, maintaining the integrity of the messages. Requires felsenstein!() to have been run first. models can either be a single model (if the messages on the tree contain just one Partition) or an array of models, if the messages have >1 Partition, or  a function that takes a node, and returns a Vector{<:BranchModel} if you need the models to vary from one branch to another.

# Keyword Arguments

  * `partition_list=nothing`: (eg. 1:3 or [1,3,5]) lets you choose which partitions to run over (but you probably want to optimize tree topology with all models, the default option).
  * `selection_rule = x -> argmax(x)`: a function that takes the current and proposed log likelihoods and selects a nni configuration. Note that the current log likelihood is stored at x[1].
  * `sort_tree=false`: determines if a [`lazysort!`](@ref) will be performed, which can reduce the amount of temporary messages that has to be initialized.
  * `traversal=Iterators.reverse`: a function that determines the traversal, permutes an iterable.
  * `shuffle=false`: do a randomly shuffled traversal, overrides `traversal`.
