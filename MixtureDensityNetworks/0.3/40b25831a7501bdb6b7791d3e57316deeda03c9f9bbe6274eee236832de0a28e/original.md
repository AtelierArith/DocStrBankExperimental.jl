```julia
generate_data(
    n_samples::Int64
) -> Tuple{Matrix{Float64}, Matrix{Float64}}

```

Generate some synthetic data for testing purposes. 

# Parameters

  * `n_samples`: The number of samples we want to generate.

# Returns

The sythetic features `X` and labels `Y` as a tuple `(X, Y)`.
