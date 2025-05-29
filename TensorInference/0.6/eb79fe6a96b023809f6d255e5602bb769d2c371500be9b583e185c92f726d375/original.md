```julia
TensorNetworkModel(
    model::TensorInference.UAIModel{ET, FT};
    openvars,
    evidence,
    optimizer,
    simplifier,
    unity_tensors_labels
) -> TensorInference.TensorNetworkModel{OMEinsum.DynamicNestedEinsum{Int64}}

```

### Keyword Arguments

  * `openvars` is the list of variables that remains in the output. If it is not empty, the return value will be a nonzero ranked tensor.
  * `evidence` is a dictionary of evidences, the values are integers start counting from 0.
  * `optimizer` is the tensor network contraction order optimizer, please check the package [`OMEinsumContractionOrders.jl`](https://github.com/TensorBFS/OMEinsumContractionOrders.jl) for available algorithms.
  * `simplifier` is some strategies for speeding up the `optimizer`, please refer the same link above.
  * `unity_tensors_labels` is a list of labels for the unity tensors. It is all single variables by default, i.e. `[[1], [2], ..., [n]]`. One can also specify multi-variables, which may increase the computational complexity.
