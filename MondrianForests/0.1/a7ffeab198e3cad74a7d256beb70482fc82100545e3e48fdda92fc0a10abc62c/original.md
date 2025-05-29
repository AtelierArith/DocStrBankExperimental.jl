```
MondrianForest(lambda::Float64, n_trees::Int, x_evals::Vector{NTuple{d,Float64}},
               X_data::Vector{NTuple{d,Float64}}, Y_data::Vector{Float64},
               estimate_var::Bool=false, significance_level::Float64=0.05) where {d}
```

Fit a Mondrian random forest to data. If `estimate_var` is `false`, do not estimate the variance or construct confidence bands. This can speed up computation significantly.

# Examples

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
