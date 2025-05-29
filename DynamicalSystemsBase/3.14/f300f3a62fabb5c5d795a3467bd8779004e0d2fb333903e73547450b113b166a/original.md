```
ParallelDynamicalSystem <: DynamicalSystem
ParallelDynamicalSystem(ds::DynamicalSystem, states::Vector{<:AbstractArray})
```

A struct that evolves several `states` of a given dynamical system in parallel **at exactly the same times**. Useful when wanting to evolve several different trajectories of the same system while ensuring that they share parameters and time vector.

This struct follows the [`DynamicalSystem`](@ref) interface with the following adjustments:

  * The function [`current_state`](@ref) is called as `current_state(pds, i::Int = 1)` which returns the `i`th state. Same for [`initial_state`](@ref).
  * Similarly, [`set_state!`](@ref) obtains a third argument `i::Int = 1` to set the `i`-th state.
  * [`current_states`](@ref) and [`initial_states`](@ref) can be used to get all parallel states.
  * [`reinit!`](@ref) takes in a vector of states (like `states`) for `u`.

```
ParallelDynamicalSystem(ds::DynamicalSystem, states::Vector{<:Dict})
```

For a dynamical system referring a MTK model, one can specify states as a vector of dictionaries to alter the current state of `ds` as in [`set_state!`](@ref).
