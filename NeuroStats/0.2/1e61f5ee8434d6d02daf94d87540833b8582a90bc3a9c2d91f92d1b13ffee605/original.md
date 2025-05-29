```
msci95(s1, s2)
```

Calculate mean difference, standard deviation and 95% confidence interval.

# Arguments

  * `s1::AbstractArray`
  * `s2::AbstractArray`

# Returns

Named tuple containing:

  * `sm::Matrix{Float64}`: mean
  * `ss::Matrix{Float64}`: standard deviation
  * `su::Matrix{Float64}`: upper 95% CI
  * `sl::Matrix{Float64}`: lower 95% CI
