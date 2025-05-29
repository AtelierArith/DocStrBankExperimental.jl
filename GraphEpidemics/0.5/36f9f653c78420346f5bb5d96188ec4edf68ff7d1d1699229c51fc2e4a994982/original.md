`init_model_discrete(model::AbstractEpiModel, g::AbstractGraph, rng::AbstractRNG, state_base::Symbol)`

Initializes all nodes to the same base state in a simulation without any active infections.

All nodes are set to `state_base`, and default values are assigned for delays, states, and infection history. Returns a `SimData` struct.
