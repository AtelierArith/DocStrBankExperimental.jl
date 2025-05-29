```
power_p2g(; <keyword arguments>)
```

Calculate study power for two proportions.

# Arguments

  * `p1::Float64`: study group 1 proportion
  * `p2::Float64`: study group 2 proportion
  * `n1::Int64`: study group 1 sample size
  * `n2::Int64`: study group 2 sample size
  * `alpha::Float64=0.05`: the probability of type I error

# Returns

  * `p::Float64`: study power
