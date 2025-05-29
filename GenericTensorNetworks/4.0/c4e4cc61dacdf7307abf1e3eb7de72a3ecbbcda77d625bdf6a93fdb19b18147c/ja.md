```julia
estimate_memory(
    problem::GenericTensorNetworks.GenericTensorNetwork,
    property::GenericTensorNetworks.AbstractProperty;
    T
) -> Any

```

特定の `property` を計算するためのメモリ推定（バイト数）を `problem` に対して行います。 `T` は基本型です。
