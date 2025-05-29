```julia
SimulationResults(
    path::AbstractString,
    name::AbstractString;
    ...
) -> PowerSimulations.SimulationResults
SimulationResults(
    path::AbstractString,
    name::AbstractString,
    execution;
    ignore_status
) -> PowerSimulations.SimulationResults

```

シミュレーション出力ディレクトリからSimulationResultsを構築します。

# 引数

  * `path::AbstractString`: シミュレーション出力ディレクトリ
  * `name::AbstractString`: シミュレーション名
  * `execution::AbstractString`: 実行番号。デフォルトは最新のものです。
  * `ignore_status::Bool`: trueの場合、シミュレーションが失敗しても結果を返します。
