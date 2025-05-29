```julia
TensorNetworkModel(
    problem::ProblemReductions.ConstraintSatisfactionProblem,
    β::Real;
    evidence,
    optimizer,
    openvars,
    simplifier,
    unity_tensors_labels
) -> TensorInference.TensorNetworkModel{OMEinsum.DynamicNestedEinsum{Int64}}

```

Convert a constraint satisfiability problem (or energy model) to a probabilistic model.

### Arguments

  * `problem` is a `ConstraintSatisfactionProblem` instance in [`ProblemReductions`](https://github.com/GiggleLiu/ProblemReductions.jl).
  * `β` is the inverse temperature.

### Keyword Arguments

  * `evidence` is a dictionary mapping variables to their values.
  * `optimizer` is the optimizer used to optimize the tensor network.
  * `openvars` is the list of variables to be marginalized.
  * `mars` is the list of variables to be marginalized.
