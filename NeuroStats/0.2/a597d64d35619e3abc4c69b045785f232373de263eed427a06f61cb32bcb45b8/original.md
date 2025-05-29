```
cir(; <keyword arguments>)
```

Calculate confidence interval for a correlation coefficient.

# Arguments

  * `r::Float64`: correlation coefficient
  * `n::Int64`: number of observations
  * `cl::Float64=0.95`: confidence level

# Returns

  * `cir::Tuple{Float64, Float64}`
