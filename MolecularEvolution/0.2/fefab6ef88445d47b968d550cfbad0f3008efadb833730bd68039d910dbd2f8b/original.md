```
cascading_max_state_dict(tree::FelNode, model; partition_list = 1:length(tree.message), node_message_dict = Dict{FelNode,Vector{<:Partition}}())
```

Takes in a tree and a model (which can be a single model, an array of models, or a function that maps FelNode->Array{<:BranchModel}), and returns a dictionary mapping nodes to their inferred ancestors under the following scheme: the state that maximizes the marginal likelihood is selected at the root, and then, for each node, the maximum likelihood state is selected conditioned on the maximized state of the parent node and the observations of all descendents. A subset of partitions can be specified by partition_list, and a dictionary can be passed in to avoid re-allocating memory, in case you're running this over and over.
