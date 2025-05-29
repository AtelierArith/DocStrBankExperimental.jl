```
lts(setting; iters = nothing, crit = 2.5, earlystop = true)
```

Perform the Fast-LTS (Least Trimmed Squares) algorithm for a given regression setting. 

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.
  * `iters::Int`: Number of iterations.
  * `crit::Float64`: Critical value.
  * `earlystop::Bool`: Early stop if the best objective does not change in iters / 2 iterations.

# Description

The algorithm searches for estimations of regression parameters which minimize the sum of first h  ordered squared residuals where h is Int(floor((n + p + 1.0) / 2.0)). Specifically, our implementation,  uses the algorithm Fast-LTS in which concentration steps are used for enlarging a basic  subset to subset of clean observation of size h.  

# Output

  * `["betas"]`: Estimated regression coefficients
  * `["S"]`: Standard error of regression
  * `["hsubset"]`: Best subset of clean observation of size h.
  * `["outliers"]`: Array of indices of outliers
  * `["scaled.residuals"]`: Array of scaled residuals
  * `["objective"]`: LTS objective value.

# Examples

```julia-repl
julia> reg = createRegressionSetting(@formula(calls ~ year), phones);
julia> lts(reg)
Dict{Any,Any} with 6 entries:
  "betas"            => [-56.5219, 1.16488]
  "S"                => 1.10918
  "hsubset"          => [11, 10, 5, 6, 23, 12, 13, 9, 24, 7, 3, 4, 8]
  "outliers"         => [14, 15, 16, 17, 18, 19, 20, 21]
  "scaled.residuals" => [2.41447, 1.63472, 0.584504, 0.61617, 0.197052, -0.222066, -0.551027, -0.970146, -0.397538, -0.185558  …  …
  "objective"        => 3.43133
```

# References

Rousseeuw, Peter J., and Katrien Van Driessen. "An algorithm for positive-breakdown  regression based on concentration steps." Data Analysis.  Springer, Berlin, Heidelberg, 2000. 335-346.
