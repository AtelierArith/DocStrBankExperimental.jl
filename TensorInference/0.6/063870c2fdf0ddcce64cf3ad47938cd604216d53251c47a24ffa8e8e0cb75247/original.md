```julia
probability(
    tn::TensorInference.TensorNetworkModel;
    usecuda,
    rescale
) -> AbstractArray

```

Contract the tensor network and return an array of probability of evidence. Precisely speaking, the return value is the partition function, which may not be l1-normalized.

If the `openvars` of the input tensor networks is zero, the array rank is zero. Otherwise, the return values corresponds to marginal probabilities.
