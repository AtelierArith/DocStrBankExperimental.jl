```julia
marginal_fobj(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult,
    num_marg::Integer,
    scale_margs::AbstractVector;
    which_point
) -> Array{Float64, 3}

```

Computes objective function at points around the minimizer.

# Required arguments

  * estset: Instance of EstimationSetup. See separate documentation [`EstimationSetup`](@ref).
  * mmsolu: Instance of EstimationResult. See separate documentation [`EstimationResult`](@ref).
  * num_marg: Number of points around optimum to evaluate.
  * scale_margs: Scale parameters for constructing grid of points to be evaluated.
