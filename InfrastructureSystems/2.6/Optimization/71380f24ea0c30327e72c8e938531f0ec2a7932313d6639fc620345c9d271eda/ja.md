```julia
read_variable(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    args...;
    kwargs...
) -> DataFrames.DataFrame

```

要求された変数キーの値を問題に対して返します。値の返却のためにキーのベクターを受け入れます。

# 引数

  * `variable::Tuple{Type{<:VariableType}, Type{<:PSY.Component}` : 望ましい結果のための変数タイプとデバイスタイプのタプル
  * `start_time::Dates.DateTime` : 要求された結果の開始時間
  * `len::Int`: 結果の長さ
