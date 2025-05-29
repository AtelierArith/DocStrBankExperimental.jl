```julia
read_parameter(
    res::PowerSimulations.SimulationProblemResults{PowerSimulations.DecisionModelSimulationResults},
    args...;
    initial_time,
    count,
    store
) -> DataStructures.SortedDict{Any, Any, Base.Order.ForwardOrdering}

```

要求されたパラメータの値を返します。複数の取得を行う際にリクエストを保持します。

# 引数

  * `args`: [`list_parameter_names`](@ref) から返された文字列または ParameterKey にスプラットできる args である可能性があります。
  * `initial_time::Dates.DateTime` : 要求された結果の初期値
  * `count::Int`: 結果の数
