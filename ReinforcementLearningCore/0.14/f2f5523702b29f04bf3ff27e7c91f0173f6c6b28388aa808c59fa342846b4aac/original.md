```
OfflineAgent(policy::AbstractPolicy, trajectory::Trajectory, offline_behavior::OfflineBehavior = OfflineBehavior()) <: AbstractAgent
```

`OfflineAgent` is an `AbstractAgent` that, unlike the usual online `Agent`, does not interact with the environment during training in order to collect data. Just like `Agent`, it contains an `AbstractPolicy` to be trained an a `Trajectory` that contains the training data. The difference being that the trajectory is filled prior to training and is not updated. An `OfflineBehavior` can optionally be provided to provide an second "behavior agent" that will generate the training data at the `PreExperimentStage`. Does nothing by default. 
