```
msci95(s1, s2)
```

Calculate mean difference, standard deviation and 95% confidence interval.

# Arguments

  * `s1::AbstractVector`
  * `s2::AbstractVector`

# Returns

Named tuple containing:

  * `sm::Float64`: mean
  * `ss::Float64`: standard deviation
  * `su::Float64`: upper 95% CI
  * `sl::Float64`: lower 95% CI
