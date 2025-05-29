```julia
serialize_results(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    directory::AbstractString
)

```

結果をバイナリファイルにシリアライズします。

`directory` はシリアライズされた OperationModel を含むディレクトリであることを推奨します。これにより、PowerSystems.System の自動デシリアライズが可能になります。`OptimizationProblemResults` インスタンスは `OptimizationProblemResults(directory)` でデシリアライズできます。
