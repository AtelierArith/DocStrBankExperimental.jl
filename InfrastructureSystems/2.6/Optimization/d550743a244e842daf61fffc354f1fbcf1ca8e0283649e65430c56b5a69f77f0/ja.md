```julia
read_duals(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    duals;
    kwargs...
) -> Dict{String, DataFrames.DataFrame}

```

要求された双対キーの値を問題に対して返します。値の返却のためにキーのベクターを受け入れます。

# 引数

  * `duals::Vector{Tuple{Type{<:ConstraintType}, Type{<:PSY.Component}}` : 希望する結果のための双対タイプとデバイスタイプのタプル
  * `start_time::Dates.DateTime` : 要求された結果の初期時間
  * `len::Int`: 結果の長さ
