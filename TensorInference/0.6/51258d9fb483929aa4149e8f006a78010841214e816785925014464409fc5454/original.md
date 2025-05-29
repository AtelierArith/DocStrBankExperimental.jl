```julia
most_probable_config(
    tn::TensorInference.TensorNetworkModel;
    usecuda
) -> Tuple{Real, Vector}

```

Returns the largest log-probability and the most probable configuration.
