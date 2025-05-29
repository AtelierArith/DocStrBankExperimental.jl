```
build_quadratic_cost_matrix(sys::ODESystem, inputs::Vector, costs::Vector{Pair}; kwargs...)
```

Assemble a quadratic cost matrix (for LQR or Kalman filtering) that penalizes states or outputs of system `sys` according to the vector of pairs `costs`.

The motivation for this function is that ModelingToolkit does not guarantee

  * Which states are selected as states after simplification.
  * The order of the states.

The second problem above, the ordering of the states, can be worked around using `reorder_states`, but the first problem cannot be solved by trivial reordering. This function thus accepts an array of costs for a user-selected state realization, and assembles the correct cost matrix for the state realization selected by MTK. To do this, the funciton performs a linearization between inputs and the cost outputs. The linearization is used to determine the matrix entries belonging to states that are not part of the realization chosen by MTK.

# Arguments:

  * `sys`: The system to be linearized (not simplified).
  * `inputs`: A vector of variables that are to be considered controlled inputs for the LQR controller.
  * `costs`: A vector of pairs.
