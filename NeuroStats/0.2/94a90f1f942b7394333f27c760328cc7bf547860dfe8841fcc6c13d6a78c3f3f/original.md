```
res_norm(x, g)
```

Test normal distribution of residuals.

# Arguments

  * `x::AbstractVector`: data values
  * `g::Vector{Int64}`: group(s) to which each data value belongs

# Returns

Named tuple containing:

  * `adt_p::Vector{Float64}`: p values for k-sample Anderson–Darling test vs normal distribution
  * `ks_p::Vector{Float64}`: p values for one-sample exact Kolmogorov–Smirnov test vs normal distribution

# Notes

p values are reported for each group and for the whole sample. If there is only one group, p values are returned only for the whole sample p values are reported.
