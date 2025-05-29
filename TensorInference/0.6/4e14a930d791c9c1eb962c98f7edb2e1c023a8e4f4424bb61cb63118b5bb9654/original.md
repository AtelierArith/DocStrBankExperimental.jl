```julia
belief_propagate(
    bp::TensorInference.BeliefPropgation;
    kwargs...
) -> Tuple{TensorInference.BPState{T, VT} where {T, VT<:Vector{T}}, TensorInference.BPInfo}

```

Run the belief propagation algorithm, and return the final state and the information about the convergence.

### Arguments

  * `bp::BeliefPropgation`: the belief propagation object

### Keyword Arguments

  * `max_iter::Int=100`: the maximum number of iterations
  * `tol::Float64=1e-6`: the tolerance for the convergence
  * `damping::Float64=0.2`: the damping factor for the message update, updated-message = damping * old-message + (1 - damping) * new-message
