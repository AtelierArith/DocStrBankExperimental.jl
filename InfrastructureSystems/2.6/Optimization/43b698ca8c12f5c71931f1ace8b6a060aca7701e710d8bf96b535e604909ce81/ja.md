```julia
read_variables(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    variables;
    kwargs...
) -> Dict{String, DataFrames.DataFrame}

```

要求された変数キーの値を問題に対して返します。値の返却のためにキーのベクターを受け入れます。

# 引数

  * `variables::Vector{Tuple{Type{<:VariableType}, Type{<:PSY.Component}}` : 希望する結果のための変数タイプとデバイスタイプのタプル
  * `start_time::Dates.DateTime` : 要求された結果の初期時間
  * `len::Int`: 結果の長さ
