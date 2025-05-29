```julia
kill_node!(
    node,
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}}
) -> Union{Nothing, Int64}

```

Removes a node from model graph. For performance reasons the function does not check if the node contains the node so it will throw an error if the user tries to delete a node which is not there. Also the node will not be deleted if the agents in the model can not be killed and the number of agents at the given node is nonzero.
