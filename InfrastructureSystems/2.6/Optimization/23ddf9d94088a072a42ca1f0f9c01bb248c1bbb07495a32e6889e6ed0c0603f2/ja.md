```julia
read_dual(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    args...;
    kwargs...
) -> DataFrames.DataFrame

```

要求されたデュアルキーの値を返します。値の返却のためにキーのベクターを受け入れます。

# 引数

  * `dual::Tuple{Type{<:ConstraintType}, Type{<:PSY.Component}` : 希望する結果のためのデュアルタイプとデバイスタイプのタプル
  * `start_time::Dates.DateTime` : 要求された結果の初期時間
  * `len::Int`: 結果の長さ
