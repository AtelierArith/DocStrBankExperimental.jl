```julia
OptimizationProblemResults(directory::AbstractString) -> Any

```

シリアライズされたディレクトリからOptimizationProblemResultsインスタンスを構築します。ソースデータを設定するのはユーザーまたは上位レベルのパッケージに任されています [`set_source_data!`](@ref) を使用して。
