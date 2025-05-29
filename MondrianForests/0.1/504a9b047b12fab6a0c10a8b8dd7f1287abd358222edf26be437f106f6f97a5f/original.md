```
select_lifetime_gcv(lambdas::Vector{Float64}, n_trees::Int,
                    X_data::Vector{NTuple{d,Float64}}, Y_data::Vector{Float64},
                    debias_order::Int, n_subsample::Int) where {d}
```

Select the lifetime parameter for a (debiased) Mondrian random forest using generalized cross-validation.

# Examples

```julia
lambdas = collect(range(0.5, 10.0, step=0.5))
n_trees = 20
debias_order = 0
n_subsample = 40
data = generate_uniform_data_uniform_errors(2, 50)
X_data = data["X"]
Y_data= data["Y"]
lambda = select_lifetime_gcv(lambdas, n_trees, X_data, Y_data, debias_order, n_subsample)
```
