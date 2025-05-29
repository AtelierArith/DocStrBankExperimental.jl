```
endpoint_conditioned_sample_state_dict(tree::FelNode, model; partition_list = 1:length(tree.message), node_message_dict = Dict{FelNode,Vector{<:Partition}}())
```

Takes in a tree and a model (which can be a single model, an array of models, or a function that maps FelNode->Array{<:BranchModel}), and draws samples under the model conditions on the leaf observations. These samples are stored in the node*message*dict, which is returned. A subset of partitions can be specified by partition_list, and a dictionary can be passed in to avoid re-allocating memory, in case you're running this over and over.
