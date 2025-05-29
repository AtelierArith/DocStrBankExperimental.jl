```
replace_profile!(prof::ProfileLikelihoodSolution, n);
    alg=get_optimiser(prof.likelihood_solution),
    conf_level::F=0.95,
    confidence_interval_method=:spline,
    threshold=get_chisq_threshold(conf_level),
    resolution=200,
    param_ranges=construct_profile_ranges(prof.likelihood_solution, get_lower_bounds(prof.likelihood_problem), get_upper_bounds(prof.likelihood_problem), resolution),
    min_steps=10,
    min_steps_fallback=:replace,
    normalise::Bool=true,
    spline_alg=FritschCarlsonMonotonicInterpolation,
    extrap=Line,
    parallel=false,
    next_initial_estimate_method=:prev,
    kwargs...) where {F}
```

Given an existing `prof::ProfileLikelihoodSolution`, replaces the profile results for the parameters in `n` by re-profiling. The keyword  arguments are the same as for [`profile`](@ref).
