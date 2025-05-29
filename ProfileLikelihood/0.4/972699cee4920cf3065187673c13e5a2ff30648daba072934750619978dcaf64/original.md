```
bivariate_profile(prob::LikelihoodProblem, sol::LikelihoodSolution, n::NTuple{M,NTuple{2,Int}};
    alg=get_optimiser(sol),
    conf_level::F=0.95,
    confidence_region_method=Val(:contour),
    threshold=get_chisq_threshold(conf_level, 2),
    resolution=200,
    grids=construct_profile_grids(n, sol, get_lower_bounds(prob), get_upper_bounds(prob), resolution),
    min_layers=10,
    outer_layers=0,
    normalise=Val(true),
    parallel=Val(false),
    next_initial_estimate_method=Val(:nearest),
    kwargs...) where {M,F}
```

Computes bivariates profile likelihoods for the parameters from a likelihood problem `prob` with MLEs `sol`. You can also call  this function using `Symbols`, e.g. if `get_syms(prob) = [:λ, :K, :u₀]`, then calling `bivariate_profile(prob, sol, ((:λ, :K), (:K, u₀)))` is the same as calling `bivariate_profile(prob, sol, ((1, 2), (2, 3)))` (the integer coordinate representation is still used in the solution, though).

For plotting, see the `plot_profiles` function (requires that you have loaded a backend of Makie.jl).

# Arguments

  * `prob::LikelihoodProblem`: The [`LikelihoodProblem`](@ref).
  * `sol::LikelihoodSolution`: The [`LikelihoodSolution`](@ref). See also [`mle`](@ref).
  * `n::NTuple{M,NTuple{2,Int}}`: The parameter indices to compute the profile likelihoods for. These should be tuples of indices, e.g. `n = ((1, 2),)` will compute the bivariate profile between the parameters `1` and `2`.

# Keyword Arguments

  * `alg=get_optimiser(sol)`: The optimiser to use for solving each optimisation problem.
  * `conf_level::F=0.95`: The level to use for the [`ConfidenceRegion`](@ref)s.
  * `confidence_region_method=:contour`: The method to use for computing the confidence regions. See also `get_confidence_regions!`. The default, `:contour`, using Contour.jl to compute the boundary of the confidence region. An alternative option is `:delaunay`, which uses DelaunayTriangulation.jl and triangulation contouring to find the boundary. This latter option is only available if you have already done `using DelaunayTriangulation`.
  * `threshold=get_chisq_threshold(conf_level, 2)`: The threshold to use for defining the confidence regions.
  * `resolution=200`: The number of points to use for defining `grids` below, giving the number of points to the left and right of each interest parameter. This can also be a vector, e.g. `resolution = [20, 50, 60]` will use `20` points for the first parameter, `50` for the second, and `60` for the third. When defining the grid between pairs of values, the maximum of the two resolutions is used (thus defining a square grid).
  * `grids=construct_profile_grids(n, sol, get_lower_bounds(prob), get_upper_bounds(prob), resolution)`: The grids to use for each parameter pair.
  * `min_layers=10`: The minimum number of layers to allow for the profile away from the MLE. If fewer than this number of layers are used before reaching the threshold, then the algorithm restarts and computes the profile likelihood a number `min_steps` of points in that direction.
  * `outer_layers=0`: The number of layers to go out away from the bounding box of the confidence region.
  * `normalise=true`: Whether to optimise the normalised profile log-likelihood or not.
  * `parallel=false`: Whether to use multithreading. If `true`, will use multithreading so that multiple parameters are profiled at once, and the work done evaluating the solution at each node in a layer is distributed across each thread.
  * `next_initial_estimate_method = :nearest`: Method for selecting the next initial estimate when stepping onto the next layer when profiling. `:nearest` simply uses the solution at the nearest node from the previous layer, but you can also use `:mle` to reuse the MLE or `:interp` to use linear interpolation. See also [`set_next_initial_estimate!`](@ref).
  * `kwargs...`: Extra keyword arguments to pass into `solve` for solving the `OptimizationProblem`. See also the docs from Optimization.jl.

# Output

Returns a [`BivariateProfileLikelihoodSolution`](@ref).
