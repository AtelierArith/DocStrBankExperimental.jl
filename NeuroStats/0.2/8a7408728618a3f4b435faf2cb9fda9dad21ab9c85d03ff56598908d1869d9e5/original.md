```
cip(p, n; <keyword arguments>)
```

Calculate confidence interval for a proportion.

# Arguments

  * `p::Float64`: proportion
  * `n::Int64`: sample size
  * `cl::Float64=0.95`: confidence level

# Returns

  * `cip::Tuple{Float64, Float64}`
