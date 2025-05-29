```
generate_noisy_data(model::Function, n::Int, np::Int, p::Int;
    x_interval::Tuple{Float64, Float64}=(-10.0, 10.0),
    θSol::Vector{Float64}=10.0 * randn(Float64, n),
    std::Float64=200.0, out_times::Float64=7.0)

generate_noisy_data(model::Function, n::Int, np::Int, p::Int,
    x_interval::Tuple{Float64, Float64})

generate_noisy_data(model::Function, n::Int, np::Int, p::Int,
    θSol::Vector{Float64}, x_interval::Tuple{Float64, Float64})
```

Random generate a fitting one-dimensional data problem.

This function receives a `model(x, θ)` function, the number of parameters `n`, the number of points `np` to be generated and the number of trusted points `p`. 

If the `n`-dimensional vector `θSol` is provided, then the exact solution will not be random generated. The interval `[xMin, xMax]` (*deprecated*) or `x_interval` for generating the values to evaluate `model` can also be provided.

It returns a tuple `(data, θSol, outliers)` where

  * `data`: (`np` x `3`) array, where each row contains `x` and `model(x, θSol)`.
  * `θSol`: `n`-dimensional vector with the exact solution.
  * `outliers`: the outliers of this data set
