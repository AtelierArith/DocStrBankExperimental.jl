```julia
read_aux_variable(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    args...;
    kwargs...
) -> DataFrames.DataFrame

```

要求された aux_variable キーの値を問題に対して返します。値の返却のためにキーのベクターを受け入れます。

# 引数

  * `aux_variable::Tuple{Type{<:AuxVariableType}, Type{<:PSY.Component}` : 希望する結果のための aux_variable タイプとデバイスタイプのタプル
  * `start_time::Dates.DateTime` : 要求された結果の初期時間
  * `len::Int`: 結果の長さ
