```julia
update_temperature(
    tnet::TensorInference.TensorNetworkModel,
    problem::ProblemReductions.ConstraintSatisfactionProblem,
    β::Real
) -> TensorInference.TensorNetworkModel

```

Update the temperature of a tensor network model. The program will regenerate tensors from the problem, without repeated optimizing the contraction order.

### Arguments

  * `tnet` is the [`TensorNetworkModel`](@ref) instance.
  * `problem` is the target constraint satisfiability problem.
  * `β` is the inverse temperature.
