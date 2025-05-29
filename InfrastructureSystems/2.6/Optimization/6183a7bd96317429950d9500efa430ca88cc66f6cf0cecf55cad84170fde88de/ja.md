```julia
read_parameters(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    parameters;
    kwargs...
) -> Dict{String, DataFrames.DataFrame}

```

要求されたパラメータキーの値を問題に対して返します。値の返却のためにキーのベクターを受け入れます。

# 引数

  * `parameters::Vector{Tuple{Type{<:ParameterType}, Type{<:PSY.Component}}` : 希望する結果のためのパラメータタイプとデバイスタイプのタプル
  * `start_time::Dates.DateTime` : 要求された結果の初期時間
  * `len::Int`: 結果の長さ
