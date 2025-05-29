```
bijames(x; <keyword arguments>)
```

Compute James' Blinding Indices.

# Arguments

  * `x::Matrix{Int64}`: 2×2 or 3×2 integer matrix of cross-tabulated counts
  * `weights::Matrix{Float64}=[0 0.5; 0.5 0; 1 1]`: use default 1996 James weights (correct guesses are assigned a weight of 0, incorrect guesses are assigned a weight of 0.5, don't know guesses are assigned a weight of 1) unless alternative weights are specified
  * `conf::Float64=0.95`: confidence level for the returned confidence intervals
  * `alternative::Symbol=:two`: type of returned confidence interval (two-sided, `:two`) or one-sided (`:less` or `:greater`)

# Returns

Named tuple containing:

  * `bi_est::Float64`: estimated value
  * `bi_se::Float64`: standard error
  * `bi_lcl::Float64`: lower confidence interval bound
  * `bi_ucl::Float64`: upper confidence interval bound

# Notes

The format of the cross-tabulated counts and weights is:

```
         Treatment  Placebo
```

Treatment    xxx        xxx  Placebo      xxx        xxx  Don't Know   xxx        xxx

If 2×2 cross-tabulated counts matrix is provided, the last row is filled with zeros.

# Sources

1. James KE, Bloch DA, Lee KK, Kraemer HC, Fuller RK. An index for assessing blindness in a multi-centre clinical trial: disulfiram for alcohol cessation–a VA cooperative study. Stat Med. 1996 Jul 15;15(13):1421-34. doi: 10.1002/(SICI)1097-0258(19960715)15:13<1421::AID-SIM266>3.0.CO;2-H. PMID: 8841652.
