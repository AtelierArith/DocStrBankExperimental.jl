```julia
estimate_memory(
    problem::GenericTensorNetworks.GenericTensorNetwork,
    property::GenericTensorNetworks.AbstractProperty;
    T
) -> Any

```

Memory estimation in number of bytes to compute certain `property` of a `problem`. `T` is the base type.
