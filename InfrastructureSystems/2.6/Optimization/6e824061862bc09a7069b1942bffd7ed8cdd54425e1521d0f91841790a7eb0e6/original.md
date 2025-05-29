```julia
serialize_results(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    directory::AbstractString
)

```

Serialize the results to a binary file.

It is recommended that `directory` be the directory that contains a serialized OperationModel. That will allow automatic deserialization of the PowerSystems.System. The `OptimizationProblemResults` instance can be deserialized with `OptimizationProblemResults(directory)`.
