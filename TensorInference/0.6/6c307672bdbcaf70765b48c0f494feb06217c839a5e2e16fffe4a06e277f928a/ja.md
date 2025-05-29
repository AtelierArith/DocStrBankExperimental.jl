```julia
get_vars(
    tn::TensorInference.TensorNetworkModel
) -> Vector{Int64}

```

このテンソルネットワークの変数を取得します。これらは脚、ラベル、または自由度とも呼ばれます。
