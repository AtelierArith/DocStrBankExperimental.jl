```
binom_test(x; verbose)
```

Test proportion against 0.5.

# Arguments

  * `x::Vector{Bool}`: vector of level 0 and 1 categories
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
