`init_model_discrete(model::AbstractEpiModel, g::AbstractGraph, nodes_active::Vector{I}, init_state_inactive::Symbol, init_state_active::Symbol, rng::AbstractRNG) where I <: Integer`

Initializes the simulation state with some nodes actively infected and others inactive.

The graph `g` provides the node structure. Nodes in `nodes_active` are assigned the `init_state_active`, while all others receive `init_state_inactive`. Delay values and infection metadata are initialized accordingly.
