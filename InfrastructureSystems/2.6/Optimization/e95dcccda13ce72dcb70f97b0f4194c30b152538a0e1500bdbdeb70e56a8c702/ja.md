```julia
read_parameter(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    args...;
    kwargs...
) -> DataFrames.DataFrame

```

要求されたパラメータキーの値を問題に対して返します。値の返却のためにキーのベクターを受け入れます。

# 引数

  * `parameter::Tuple{Type{<:ParameterType}, Type{<:PSY.Component}` : 希望する結果のためのパラメータタイプとデバイスタイプのタプル
  * `start_time::Dates.DateTime` : 要求された結果の初期時間
  * `len::Int`: 結果の長さ
