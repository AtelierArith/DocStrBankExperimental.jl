```julia
get_decision_problem_results(
    results::PowerSimulations.SimulationResults,
    problem::String;
    populate_system,
    populate_units
) -> PowerSimulations.SimulationProblemResults{PowerSimulations.DecisionModelSimulationResults}

```

シミュレーション結果に対応するSimulationProblemResultsを返します

# 引数

  * `sim_results::PSI.SimulationResults`: 読み取るシミュレーション結果
  * `problem::String`: 問題の名前（例: "UC", "ED"）
  * `populate_system::Bool = true`: 結果のシステムを[`get_system!`](@ref)を使用しているかのように設定するかどうか
  * `populate_units::Union{IS.UnitSystem, String, Nothing} = IS.UnitSystem.NATURAL_UNITS`: 結果のシステムを設定するための単位系（必要に応じて、`populate_system=true`が必要）
