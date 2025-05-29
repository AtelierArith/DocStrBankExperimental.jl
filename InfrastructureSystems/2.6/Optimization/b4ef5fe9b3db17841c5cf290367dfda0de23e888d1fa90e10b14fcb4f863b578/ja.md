```julia
read_aux_variables(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    aux_variables;
    kwargs...
) -> Dict{String, DataFrames.DataFrame}

```

要求された aux_variable キーの値を問題に対して返します。値の返却のためにキーのベクターを受け入れます。

# 引数

  * `aux_variables::Vector{Tuple{Type{<:AuxVariableType}, Type{<:PSY.Component}}` : 求める結果のための aux_variable タイプとデバイスタイプのタプル
  * `start_time::Dates.DateTime` : 求める結果の初期時間
  * `len::Int`: 結果の長さ
