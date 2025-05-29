```julia
update_evidence!(
    tnet::TensorInference.TensorNetworkModel,
    evidence::Dict
) -> TensorInference.TensorNetworkModel

```

Update the evidence of a tensor network model, without changing the set of observed variables!

### Arguments

  * `tnet` is the [`TensorNetworkModel`](@ref) instance.
  * `evidence` is the new evidence, the keys must be a subset of existing evidence.
