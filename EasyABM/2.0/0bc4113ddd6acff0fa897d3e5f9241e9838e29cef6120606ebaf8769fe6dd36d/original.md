```julia
kill_agent!(
    agent::EasyABM.AbstractAgent,
    model::EasyABM.AbstractSpaceModel{EasyABM.MortalType}
) -> Union{Nothing, Int64}

```

Sets the agent as inactive thus effectively removing from the model. However, the removed agents  are permanently removed from the list `model.agents` only once after the `step_rule`.
