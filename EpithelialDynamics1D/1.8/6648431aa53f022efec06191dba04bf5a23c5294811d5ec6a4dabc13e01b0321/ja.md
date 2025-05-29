```
leading_edges(sol::EnsembleSolution; indices = eachindex(sol), alpha=0.05)
```

`EnsembleSolution` から [`CellProblem`](@ref) へのリーディングエッジの要約統計を計算します。

# 引数

  * `sol::EnsembleSolution`: `CellProblem` に対するアンサンブルソリューション。

# キーワード引数

  * `indices = eachindex(sol)`: 考慮するセルシミュレーションのインデックス。
  * `alpha::Float64 = 0.05`: 信頼区間の有意水準。

# 出力

  * `L::Vector{Vector{Float64}}`: 各セルシミュレーションのリーディングエッジ。
  * `means::Vector{Float64}`: 各セルシミュレーションの平均リーディングエッジ。
  * `lowers::Vector{Float64}`: 各セルシミュレーションのリーディングエッジの信頼区間の下限。
  * `uppers::Vector{Float64}`: 各セルシミュレーションのリーディングエッジの信頼区間の上限。
