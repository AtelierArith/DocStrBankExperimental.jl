```julia
export_optimizer_stats(
    res::InfrastructureSystems.Results,
    directory::AbstractString;
    format
) -> Any

```

最適化統計をCSVまたはJSONに保存します

# 引数

  * `res::Union{OptimizationProblemResults, SimulationProblmeResults`: 結果
  * `directory::AbstractString` : 対象ディレクトリ
  * `format = "CSV"` : "csv"または"json"を指定できます
