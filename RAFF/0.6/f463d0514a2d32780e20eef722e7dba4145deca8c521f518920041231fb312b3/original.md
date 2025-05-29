```
generate_clustered_noisy_data!(data::Array{Float64, 2},
    v::Vector{Int}, model::Function, n::Int, np::Int, p::Int,
    x_interval::Tuple{Float64,Float64},
    cluster_interval::Tuple{Float64, Float64}; kwargs...)
```

Generate a test set with clustered outliers. This version overwrites the content of (`np` x `3`) matrix `data` and vector `v` with integer indices to the position of outliers in `data`.

The arguments and optional arguments are the same for [`generate_noisy_data!`](@ref), with exception of tuple `cluster_interval` which is the interval to generate the clustered outliers.

It returns a tuple `(data, θSol, outliers)` where

  * `data`: (`np` x `3`) array, where each row contains `x` and `model(x, θSol)`. The same array given as argument
  * `θSol`: `n`-dimensional vector with the exact solution.
  * `outliers`: the outliers of this data set. The same vector given as argument.
