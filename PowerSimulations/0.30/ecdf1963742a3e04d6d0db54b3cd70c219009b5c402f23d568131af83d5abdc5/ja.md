```julia
read_dual(
    res::PowerSimulations.SimulationProblemResults{PowerSimulations.DecisionModelSimulationResults},
    args...;
    initial_time,
    count,
    store
) -> DataStructures.SortedDict{Any, Any, Base.Order.ForwardOrdering}

```

要求されたデュアルの値を返します。複数の取得を行う際にリクエストを保持します。

# 引数

  * `args`: [`list_dual_names`](@ref) から返された文字列または ConstraintKey にスプラットできる引数。
  * `initial_time::Dates.DateTime` : 要求された結果の初期値
  * `count::Int`: 結果の数
  * `store::SimulationStore`: 読み取り用に開かれたストア
