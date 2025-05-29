```
bibang(x; <keyword arguments>)
```

Compute Bang's Blinding Indices.

# Arguments

  * `x::Matrix{Int64}`: 2×2 or 3×2 integer matrix of cross-tabulated counts
  * `weights::Matrix{Float64}=[0 0.5; 0.5 0; 1 1]`: use default 1996 James weights (correct guesses are assigned a weight of 0, incorrect guesses are assigned a weight of 0.5, don't know guesses are assigned a weight of 1) unless alternative weights are specified
  * `conf::Float64=0.95`: confidence level for the returned confidence intervals
  * `alternative::Symbol=:two`: type of returned confidence interval (two-sided, `:two`) or one-sided (`:less` or `:greater`)

# Returns

Named tuple containing:

  * `bi_est::Float64`: estimated values for group 1 and 2
  * `bi_se::Float64`: standard errors for group 1 and 2
  * `bi_lcl::Float64`: lower confidence interval bounds for group 1 and 2
  * `bi_ucl::Float64`: upper confidence interval bounds for group 1 and 2

# Notes

The format of the cross-tabulated counts and weights is:

```
         Treatment  Placebo
```

Treatment    xxx        xxx  Placebo      xxx        xxx  Don't Know   xxx        xxx

If 2×2 cross-tabulated counts matrix is provided, the last row is filled with zeros.

# Sources

1. Bang H, Ni L, Davis CE. Assessment of blinding in clinical trials. Control Clin Trials. 2004 Apr;25(2):143-56. doi: 10.1016/j.cct.2003.10.016. PMID: 15020033.
