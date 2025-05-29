```
OfflineBehavior(; agent:: Union{<:Agent, Nothing}, steps::Int, reset_condition)
```

Used to provide an OfflineAgent with a "behavior agent" that will generate the training data at the `PreExperimentStage`. If `agent` is `nothing` (by default), does nothing. The `trajectory` of agent should  be the same as that of the parent `OfflineAgent`. `steps` is the number of data elements to generate, defaults to the capacity of the trajectory. `reset_condition` is the episode reset condition for the data generation (defaults to `ResetIfEnvTerminated()`).

The behavior agent will interact with the main environment of the experiment to generate the data.
