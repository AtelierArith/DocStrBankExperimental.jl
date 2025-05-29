```
size_p1g(; <keyword arguments>)
```

Calculate required sample size for a proportion (group 1 vs population).

# Arguments

  * `p1::Float64`: population proportion
  * `p2::Float64`: study group proportion
  * `alpha::Float64=0.05`: the probability of type I error
  * `power::Float64=0.8`: the ability to detect a difference between groups (power = 1 - beta, where beta is the probability of type II error)

# Returns

  * `n::Int64`: group 1 sample size
