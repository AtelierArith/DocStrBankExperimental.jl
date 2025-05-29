```julia
sampleTF(
    tf::MPIFiles.TransferFunction,
    f::MPIFiles.MPIFile;
    numPeriodGrouping
) -> Any

```

Sample the `tf` at the frequencies defined by the measurement `f`, optionally with `numPeriodGrouping`
