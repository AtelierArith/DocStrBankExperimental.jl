sample*down!(root::FelNode,models,partition*list)

Generates samples under the model. The root.parent*message is taken as the starting distribution, and node.message contains the sampled messages. models can either be a single model (if the messages on the tree contain just one Partition) or an array of models, if the messages have >1 Partition, or  a function that takes a node, and returns a Vector{<:BranchModel} if you need the models to vary from one branch to another. partition*list (eg. 1:3 or [1,3,5]) lets you choose which partitions to run over.
