```
binom_test(p, n; verbose)
```

Test proportion against 0.5.

# Arguments

  * `p::Float64`: proportion of level 1 observations
  * `n::Int64`: number of observations
  * `verbose::Bool=true`: print detailed output

# Returns

Named tuple containing:

  * `x0::Int64`: level 0 counts
  * `x1::Int64`: level 1 counts
  * `p0::Float64`: level 0 proportion
  * `p1::Float64`: level 1 proportion
  * `ci0::Tuple{Float64, Float64}`: level 1 proportion 95%CI
  * `ci1::Tuple{Float64, Float64}`: level 1 proportion 95%CI
  * `p::Float64`: Binomial test p value
