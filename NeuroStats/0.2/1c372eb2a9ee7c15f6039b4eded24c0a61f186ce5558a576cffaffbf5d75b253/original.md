```
power_p1g(; <keyword arguments>)
```

Calculate study power for one proportion.

# Arguments

  * `p1::Float64`: study group proportion
  * `p2::Float64`: population proportion
  * `n1::Int64`: study group sample size
  * `alpha::Float64=0.05`: the probability of type I error

# Returns

  * `p::Float64`: study power
