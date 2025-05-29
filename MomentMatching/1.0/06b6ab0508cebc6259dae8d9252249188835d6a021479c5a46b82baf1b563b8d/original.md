```julia
marginal_fobj(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult;
    which_point,
    gridx
) -> Array{Float64, 3}

```

Computes objective function at points around the minimizer.

# Required arguments

  * estset: Instance of EstimationSetup. See separate documentation [`EstimationSetup`](@ref).
  * mmsolu: Instance of EstimationResult. See separate documentation [`EstimationResult`](@ref).

# Optional arguments

  * gridx: Grid of points around of optimum to evaluate objective function at.
