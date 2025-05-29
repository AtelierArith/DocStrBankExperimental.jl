```
refine_profile!(prof::ProfileLikelihoodSolution, n;
    alg=get_optimiser(prof.likelihood_solution),
    conf_level::F=0.95,
    confidence_interval_method=:spline,
    threshold=get_chisq_threshold(conf_level),
    target_number=10,
    normalise::Bool=true,
    spline_alg=FritschCarlsonMonotonicInterpolation,
    extrap=Line,
    parallel=false,
    kwargs...) where {F}
```

Given an existing `prof::ProfileLikelihoodSolution`, refines the profile results for the parameters in `n` by adding more points. The keyword  arguments are the same as for [`profile`](@ref). `target_number` is the total number of points that should be included in the end (not how many more  are added).
