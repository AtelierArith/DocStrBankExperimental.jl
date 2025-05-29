```
build_quadratic_cost_matrix(linear_sys, ssys::ODESystem, costs::Vector{Pair})
```

For a system that has been linearized, assemble a quadratic cost matrix (for LQR or Kalman filtering) that penalizes states or outputs of simplified system `ssys` according to the vector of pairs `costs`.

The motivation for this function is that ModelingToolkit does not guarantee

  * Which states are selected as states after simplification.
  * The order of the states.

The second problem above, the ordering of the states, can be worked around using `reorder_states`, but the first problem cannot be solved by trivial reordering. This function thus accepts an array of costs for a user-selected state realization, and assembles the correct cost matrix for the state realization selected by MTK. To do this, the funciton needs the linearization (`linear_sys`) as well as the simplified system, both of which are outputs of [`linearize`](@ref).

# Arguments:

  * `linear_sys`: Output of [`linearize`](@ref), an object containing a property called `C`. This can be a [`ControlSystemsBase.StateSpace`](@ref) or a `NamedTuple` with a field `C`.
  * `ssys`: Output of [`linearize`](@ref).
  * `costs`: A vector of pairs
