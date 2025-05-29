```julia
combine(
    tf1::MPIFiles.TransferFunction,
    tf2::MPIFiles.TransferFunction;
    interpolate
) -> Any

```

Combine two `TransferFunctions` along their channel dimension. If interpolate=false, will only work if the frequency samples are identical.
