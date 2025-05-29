```julia
default_weight_matrix(
    mode::MomentMatching.EstimationMode,
    typemom::String,
    n::Integer
) -> Matrix{Float64}

```

Set up default weighting matrix to compute the objective function. Should be defined for any subtype of [`EstimationMode`](@ref) else returns unitary matrix.
