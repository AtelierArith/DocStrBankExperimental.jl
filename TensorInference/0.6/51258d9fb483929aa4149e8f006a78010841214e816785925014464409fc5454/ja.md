```julia
most_probable_config(
    tn::TensorInference.TensorNetworkModel;
    usecuda
) -> Tuple{Real, Vector}

```

最も大きな対数確率と最も可能性の高い構成を返します。
