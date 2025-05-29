```
lta(setting; exact = false, earlystop = true)
```

Perform the Hawkins & Olive (1999) algorithm (Least Trimmed Absolute Deviations)  for the given regression setting.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.
  * `exact::Bool`: Consider all possible subsets of p or not where p is the number of regression parameters.
  * `earlystop::Bool`: Early stop if the best objective does not change in number of remaining iters / 5 iterations.

# Description

`lta` is a trimmed version of `lad` in which the sum of first h absolute residuals is minimized where h is Int(floor((n + p + 1.0) / 2.0)). 

# Output

  * `["betas"]`: Estimated regression coefficients
  * `["objective]`: Objective value

# Examples

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> lta(reg0001)
Dict{Any,Any} with 2 entries:
  "betas"     => [-55.5, 1.15]
  "objective" => 5.7

julia> lta(reg0001, exact = true)
Dict{Any,Any} with 2 entries:
  "betas"     => [-55.5, 1.15]
  "objective" => 5.7  
```

# References

Hawkins, Douglas M., and David Olive. "Applications and algorithms for least trimmed sum of  absolute deviations regression." Computational Statistics & Data Analysis 32.2 (1999): 119-134.
