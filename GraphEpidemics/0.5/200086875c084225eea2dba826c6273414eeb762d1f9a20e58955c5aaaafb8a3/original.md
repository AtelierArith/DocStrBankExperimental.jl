`set_state_nodes(model::AbstractEpiModel, data::SimData, rng::AbstractRNG, nodes::Vector{I}, state::Symbol, active::Bool; tset::Integer=0) where I <: Integer`

Assigns a state to specified nodes and activates them if necessary.

Updates the states of all nodes in `nodes` to `state`. If the state is marked as active or `active` is true, it updates infection metadata and transition delays using the model and random number generator.

### Optional Arguments

  * `tset`: The time to assign for infection and transition tracking (default: 0).
