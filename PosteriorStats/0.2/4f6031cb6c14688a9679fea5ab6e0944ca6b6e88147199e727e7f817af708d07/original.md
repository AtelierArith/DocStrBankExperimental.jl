```
summarize(data, stats_funs...; name="SummaryStats", [var_names]) -> SummaryStats
```

Compute the summary statistics in `stats_funs` on each param in `data`.

`stats_funs` is a collection of functions that reduces a matrix with shape `(draws, chains)` to a scalar or a collection of scalars. Alternatively, an item in `stats_funs` may be a `Pair` of the form `name => fun` specifying the name to be used for the statistic or of the form `(name1, ...) => fun` when the function returns a collection. When the function returns a collection, the names in this latter format must be provided.

If no stats functions are provided, then those specified in [`default_summary_stats`](@ref) are computed.

`var_names` specifies the names of the parameters in `data`. If not provided, the names are inferred from `data`.

To support computing summary statistics from a custom object, overload this method specifying the type of `data`.

See also [`SummaryStats`](@ref), [`default_summary_stats`](@ref), [`default_stats`](@ref), [`default_diagnostics`](@ref).

# Examples

Compute `mean`, `std` and the Monte Carlo standard error (MCSE) of the mean estimate:

```jldoctest summarize; setup = (using Random; Random.seed!(84))
julia> using Statistics, StatsBase

julia> x = randn(1000, 4, 3) .+ reshape(0:10:20, 1, 1, :);

julia> summarize(x, mean, std, :mcse_mean => sem; name="Mean/Std")
Mean/Std
       mean    std  mcse_mean
 1   0.0003  0.989      0.016
 2  10.02    0.988      0.016
 3  19.98    0.988      0.016
```

Avoid recomputing the mean by using `mean_and_std`, and provide parameter names:

```jldoctest summarize
julia> summarize(x, (:mean, :std) => mean_and_std, mad; var_names=[:a, :b, :c])
SummaryStats
         mean    std    mad
 a   0.000275  0.989  0.978
 b  10.0       0.988  0.995
 c  20.0       0.988  0.979
```

Note that when an estimator and its MCSE are both computed, the MCSE is used to determine the number of significant digits that will be displayed.

```jldoctest summarize
julia> summarize(x; var_names=[:a, :b, :c])
SummaryStats
       mean   std  hdi_3%  hdi_97%  mcse_mean  mcse_std  ess_tail  ess_bulk  r ⋯
 a   0.0003  0.99   -1.92     1.78      0.016     0.012      3567      3663  1 ⋯
 b  10.02    0.99    8.17    11.9       0.016     0.011      3841      3906  1 ⋯
 c  19.98    0.99   18.1     21.9       0.016     0.012      3892      3749  1 ⋯
                                                                1 column omitted
```

Compute just the statistics with an 89% HDI on all parameters, and provide the parameter names:

```jldoctest summarize
julia> summarize(x, default_stats(; prob_interval=0.89)...; var_names=[:a, :b, :c])
SummaryStats
         mean    std  hdi_5.5%  hdi_94.5%
 a   0.000275  0.989     -1.63       1.52
 b  10.0       0.988      8.53      11.6
 c  20.0       0.988     18.5       21.6
```

Compute the summary stats focusing on `Statistics.median`:

```jldoctest summarize
julia> summarize(x, default_summary_stats(median)...; var_names=[:a, :b, :c])
SummaryStats
    median    mad  eti_3%  eti_97%  mcse_median  ess_tail  ess_median  rhat
 a   0.004  0.978   -1.83     1.89        0.020      3567        3336  1.00
 b  10.02   0.995    8.17    11.9         0.023      3841        3787  1.00
 c  19.99   0.979   18.1     21.9         0.020      3892        3829  1.00
```
