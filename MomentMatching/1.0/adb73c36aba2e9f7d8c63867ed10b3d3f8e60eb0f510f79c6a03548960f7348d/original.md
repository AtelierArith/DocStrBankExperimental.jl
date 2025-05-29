```julia
defaultxgrid(
    x::Vector{Float64};
    num_marg,
    scale_margs
) -> Matrix{Float64}

```

Computes objective function at points around the minimizer.

# Required arguments

  * x: Array with parameter estimates.
  * num_marg: Number of points around optimum to evaluate.
  * scale_margs: Scale parameters for constructing grid of points to be evaluated.
