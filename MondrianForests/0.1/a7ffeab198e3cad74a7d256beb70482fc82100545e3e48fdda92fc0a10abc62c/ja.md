```
MondrianForest(lambda::Float64, n_trees::Int, x_evals::Vector{NTuple{d,Float64}},
               X_data::Vector{NTuple{d,Float64}}, Y_data::Vector{Float64},
               estimate_var::Bool=false, significance_level::Float64=0.05) where {d}
```

データに対してモンドリアンランダムフォレストをフィットさせます。`estimate_var`が`false`の場合、分散を推定したり信頼区間を構築したりしません。これにより計算が大幅に高速化される可能性があります。

# 例

```julia
lambda = 3.0
n_trees = 20
x_evals = [(0.5, 0.5), (0.2, 0.8)]
data = generate_uniform_data_uniform_errors(2, 50)
X_data = data["X"]
Y_data= data["Y"]
estimate_var = true
significance_level = 0.05
forest = MondrianForest(lambda, n_trees, x_evals, X_data, Y_data,
                        estimate_var, significance_level)
```
