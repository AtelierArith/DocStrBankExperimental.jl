```
branchlength_optim!(tree::FelNode, models;  <keyword arguments>)
```

Uses golden section search, or optionally Brent's method, to optimize all branches recursively, maintaining the integrity of the messages. Requires felsenstein!() to have been run first. models can either be a single model (if the messages on the tree contain just one Partition) or an array of models, if the messages have >1 Partition, or  a function that takes a node, and returns a Vector{<:BranchModel} if you need the models to vary from one branch to another.

# Keyword Arguments

  * `partition_list=nothing`: (eg. 1:3 or [1,3,5]) lets you choose which partitions to run over (but you probably want to optimize branch lengths with all models, the default option).
  * `tol=1e-5`: absolute tolerance for the `bl_optimizer`.
  * `bl_optimizer::UnivariateModifier=GoldenSectionOpt()`: the algorithm used to optimize the log likelihood of a branch length. In addition to golden section search, Brent's method can be used by setting `bl_optimizer=BrentsMethodOpt()`.
  * `sort_tree=false`: determines if a [`lazysort!`](@ref) will be performed, which can reduce the amount of temporary messages that has to be initialized.
  * `traversal=Iterators.reverse`: a function that determines the traversal, permutes an iterable.
  * `shuffle=false`: do a randomly shuffled traversal, overrides `traversal`.
