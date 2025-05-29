```
get_gcv(lambda::Float64, n_trees::Int,
        X_data::Vector{NTuple{d,Float64}}, Y_data::Vector{Float64},
        debias_order::Int, n_subsample::Int) where {d}
```

Get the generalized cross-validation score of a lifetime parameter lambda.

# Examples

```julia
lambda = 3.0
n_trees = 20
debias_order = 0
n_subsample = 40
data = generate_uniform_data_uniform_errors(2, 50)
X_data = data["X"]
Y_data= data["Y"]
lambda = get_gcv(lambdas, n_trees, X_data, Y_data, debias_order, n_subsample)
```
