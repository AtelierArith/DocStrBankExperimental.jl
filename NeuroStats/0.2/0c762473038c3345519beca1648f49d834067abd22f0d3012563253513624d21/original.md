```
size_p2g(; <keyword arguments>)
```

Calculate required sample size for a proportion (group 1 vs group 2).

# Arguments

  * `p1::Float64`: study group 1 proportion
  * `p2::Float64`: study group 2 proportion
  * `r::Int64=1`: enrollment ratio – the ratio of group 2 to group 1 enrollment
  * `alpha::Float64=0.05`: the probability of type I error
  * `power::Float64=0.8`: the ability to detect a difference between groups (power = 1 - beta, where beta is the probability of type II error)

# Returns

Named tuple containing:

  * `n1::Int64`: group 1 sample size
  * `n2::Int64`: group 2 sample size
