```
size_c1g(; <keyword arguments>)
```

Calculate required sample size for a continuous variable (group 1 vs population).

# Arguments

  * `m::Real`: population mean
  * `s::Real`: population standard deviation
  * `xbar::Real`: study group mean
  * `alpha::Float64=0.05`: the probability of type I error
  * `power::Float64=0.8`: the ability to detect a difference between groups (power = 1 - beta, where beta is the probability of type II error)
  * `iter::Bool=false`: use iterative method

# Returns

  * `n::Int64`: group sample size
