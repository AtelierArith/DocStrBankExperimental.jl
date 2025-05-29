```
p = profile_solvers(stats, costs, costnames;
                    width = 400, height = 400,
                    b = PlotsBackend(), kwargs...)
```

Produce performance profiles comparing `solvers` based on the data in `stats`.

Inputs:

  * `stats::Dict{Symbol,DataFrame}`: a dictionary of `DataFrame`s containing the   benchmark results per solver (e.g., produced by `bmark_results_to_dataframes()`)
  * `costs::Vector{Function}`: a vector of functions specifying the measures to use in the profiles
  * `costnames::Vector{String}`: names to be used as titles of the profiles.

Keyword inputs:

  * `width::Int`: Width of each individual plot (Default: 400)
  * `height::Int`: Height of each individual plot (Default: 400)
  * `b::BenchmarkProfiles.AbstractBackend` : backend used for the plot.

Additional `kwargs` are passed to the `plot` call.

Output: A Plots.jl plot representing a set of performance profiles comparing the solvers. The set contains performance profiles comparing all the solvers together on the measures given in `costs`. If there are more than two solvers, additional profiles are produced comparing the solvers two by two on each cost measure.
