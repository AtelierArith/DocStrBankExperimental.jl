```
cir(x, y; <keyword arguments>)
```

Calculate confidence interval for a correlation coefficient.

# Arguments

  * `x::AbstractVector`
  * `y::AbstractVector`
  * `cl::Float64=0.95`: confidence level

# Returns

  * `cir::Tuple{Float64, Float64}`
