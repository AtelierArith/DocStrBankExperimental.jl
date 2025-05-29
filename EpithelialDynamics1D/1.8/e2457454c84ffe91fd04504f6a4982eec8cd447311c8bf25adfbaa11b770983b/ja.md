```
cell_numbers(sol::EnsembleSolution; indices = eachindex(sol), alpha=0.05)
```

`EnsembleSolution`からの細胞数の要約統計を計算します [`CellProblem`](@ref)。

# 引数

  * `sol::EnsembleSolution`: `CellProblem`へのアンサンブルソリューション。

# キーワード引数

  * `indices = eachindex(sol)`: 考慮する細胞シミュレーションのインデックス。
  * `alpha::Float64 = 0.05`: 信頼区間の有意水準。

# 出力

  * `N::Vector{Vector{Int}}`: 各細胞シミュレーションの細胞数。
  * `means::Vector{Float64}`: 各細胞シミュレーションの平均細胞数。
  * `lowers::Vector{Float64}`: 各細胞シミュレーションの細胞数の信頼区間の下限。
  * `uppers::Vector{Float64}`: 各細胞シミュレーションの細胞数の信頼区間の上限。
