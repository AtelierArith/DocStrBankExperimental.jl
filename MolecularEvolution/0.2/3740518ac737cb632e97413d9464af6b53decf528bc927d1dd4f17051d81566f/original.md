```
marginal_state_dict(tree::FelNode, model; partition_list = 1:length(tree.message), node_message_dict = Dict{FelNode,Vector{<:Partition}}())
```

Takes in a tree and a model (which can be a single model, an array of models, or a function that maps FelNode->Array{<:BranchModel}), and returns a dictionary mapping nodes to their marginal reconstructions (ie. P(state|all observations,model)). A subset of partitions can be specified by partition_list, and a dictionary can be passed in to avoid re-allocating memory, in case you're running this over and over.
