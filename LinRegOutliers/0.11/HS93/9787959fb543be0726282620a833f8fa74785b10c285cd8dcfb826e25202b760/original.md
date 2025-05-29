```
hs93(setting; alpha = 0.05, basicsubsetindices = nothing)
```

Perform the Hadi & Simonoff (1993) algorithm for the given regression setting.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.
  * `alpha::Float64`: Optional argument of the probability of rejecting the null hypothesis.
  * `basicsubsetindices::Array{Int, 1}`: Initial basic subset, by default, the algorithm creates an initial set of clean observations.

# Description

Performs a forward search by selecting and enlarging an initial clean subset of observations and  iterates until scaled residuals exceeds a threshold.

# Output

  * `["outliers"]`: Array of indices of outliers
  * `["t"]`: Threshold, specifically, calculated quantile of a Student-T distribution
  * `["d"]`: Internal and external scaled residuals.
  * `["betas"]: Vector of estimated regression coefficients.
  * `["converged"]: Boolean value indicating whether the algorithm converged or not.

# Examples

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> hs93(reg0001)
Dict{Any,Any} with 3 entries:
  "outliers" => [14, 15, 16, 17, 18, 19, 20, 21]
  "t"        => -3.59263
  "d"        => [2.04474, 1.14495, -0.0633255, 0.0632934, -0.354349, -0.766818, -1.06862, -1.47638, -0.7…
  "converged"=> true
```

# References

Hadi, Ali S., and Jeffrey S. Simonoff. "Procedures for the identification of  multiple outliers in linear models." Journal of the American Statistical  Association 88.424 (1993): 1264-1272.
