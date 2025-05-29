```julia
read_expression(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    args...;
    kwargs...
) -> DataFrames.DataFrame

```

要求された式キーの値を問題に対して返します。値の返却のためにキーのベクターを受け入れます。

# 引数

  * `expression::Tuple{Type{<:ExpressionType}, Type{<:PSY.Component}` : 希望する結果のための式タイプとデバイスタイプのタプル
  * `start_time::Dates.DateTime` : 要求された結果の初期時間
  * `len::Int`: 結果の長さ
