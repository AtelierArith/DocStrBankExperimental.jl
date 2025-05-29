```
profile(prob::LikelihoodProblem, sol::LikelihoodSolution, n=1:number_of_parameters(prob);
    alg=get_optimiser(sol),
    conf_level::F=0.95,
    confidence_interval_method=:spline,
    threshold=get_chisq_threshold(conf_level),
    resolution=200,
    param_ranges=construct_profile_ranges(sol, get_lower_bounds(prob), get_upper_bounds(prob), resolution),
    min_steps=10,
    normalise::Bool=true,
    spline_alg=FritschCarlsonMonotonicInterpolation,
    extrap=Line,
    parallel=false,
    next_initial_estimate_method = :prev,
    kwargs...)
```

Computes profile likelihoods for the parameters from a likelihood problem `prob` with MLEs `sol`.

See also [`replace_profile!`](@ref) which allows you to re-profile a parameter in case you are not satisfied with  the results. For plotting, see the `plot_profiles` function (requires that you have loaded a backend of Makie.jl).

# Arguments

  * `prob::LikelihoodProblem`: The [`LikelihoodProblem`](@ref).
  * `sol::LikelihoodSolution`: The [`LikelihoodSolution`](@ref). See also [`mle`](@ref).
  * `n=1:number_of_parameters(prob)`: The parameter indices to compute the profile likelihoods for.

# Keyword Arguments

  * `alg=get_optimiser(sol)`: The optimiser to use for solving each optimisation problem.
  * `conf_level::F=0.95`: The level to use for the [`ConfidenceInterval`](@ref)s.
  * `confidence_interval_method=:spline`: The method to use for computing the confidence intervals. See also [`get_confidence_intervals!`](@ref). The default `:spline` uses rootfinding on the spline through the data, defining a continuous function, while the alternative `:extrema` simply takes the extrema of the values that exceed the threshold.
  * `threshold=get_chisq_threshold(conf_level)`: The threshold to use for defining the confidence intervals.
  * `resolution=200`: The number of points to use for evaluating the profile likelihood in each direction starting from the MLE (giving a total of `2resolution` points). - `resolution=200`: The number of points to use for defining `grids` below, giving the number of points to the left and right of each interest parameter. This can also be a vector, e.g. `resolution = [20, 50, 60]` will use `20` points for the first parameter, `50` for the second, and `60` for the third.
  * `param_ranges=construct_profile_ranges(sol, get_lower_bounds(prob), get_upper_bounds(prob), resolution)`: The ranges to use for each parameter.
  * `min_steps=10`: The minimum number of steps to allow for the profile in each direction. If fewer than this number of steps are used before reaching the threshold, then the algorithm restarts and computes the profile likelihood a number `min_steps` of points in that direction. See also `min_steps_fallback`.
  * `min_steps_fallback=:replace`: Method to use for updating the profile when it does not reach the minimum number of steps, `min_steps`. See also [`reach_min_steps!`](@ref). If `:replace`, then the profile is completely replaced and we use `min_steps` equally spaced points to replace it. If `:refine`, we just fill in some of the space in the grid so that a `min_steps` number of points are reached. Note that this latter option will mean that the spacing is no longer constant between parameter values. You can use `:refine_parallel` to apply `:refine` in parallel.
  * `normalise::Bool=true`: Whether to optimise the normalised profile log-likelihood or not.
  * `spline_alg=FritschCarlsonMonotonicInterpolation`: The interpolation algorithm to use for computing a spline from the profile data. See Interpolations.jl.
  * `extrap=Line`: The extrapolation algorithm to use for computing a spline from the profile data. See Interpolations.jl.
  * `parallel=false`: Whether to use multithreading. If `true`, will use multithreading so that multiple parameters are profiled at once, and the steps to the left and right are done at the same time.
  * `next_initial_estimate_method = :prev`: Method for selecting the next initial estimate when stepping forward when profiling. `:prev` simply uses the previous solution, but you can also use `:interp` to use linear interpolation. See also [`set_next_initial_estimate!`](@ref).
  * `kwargs...`: Extra keyword arguments to pass into `solve` for solving the `OptimizationProblem`. See also the docs from Optimization.jl.

# Output

Returns a [`ProfileLikelihoodSolution`](@ref).
