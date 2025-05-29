```
statuses, avgs = quick_summary(stats; kwargs...)
```

Call `count_unique` and compute a few average measures for each solver in `stats`.

#### Arguments

  * `stats::Dict{Symbol,DataFrame}`: benchmark statistics such as returned by `bmark_solvers`.

#### Keyword arguments

  * `cols::Vector{Symbol}`: symbols indicating `DataFrame` columns in solver statistics for which we compute averages. Default: `[:iter, :neval_obj, :neval_grad, :neval_hess, :neval_hprod, :elapsed_time]`.

#### Return value

  * `statuses::Dict{Symbol,Dict{Symbol,Int}}`: a dictionary of number of occurrences of each final status for each solver in `stats`. Each value in this dictionary is returned by `count_unique`
  * `avgs::Dict{Symbol,Dict{Symbol,Float64}}`: a dictionary that contains averages of performance measures across all problems for each solver. Each `avgs[solver]` is a `Dict{Symbol,Float64}` where the measures are those given in the keyword argument `cols` and values are averages of those measures across all problems.

Example: the snippet

```
statuses, avgs = quick_summary(stats)
for solver ∈ keys(stats)
  @info "statistics for" solver statuses[solver] avgs[solver]
end
```

displays quick summary and averages for each solver.
