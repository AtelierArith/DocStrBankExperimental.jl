```
power_c2g(; <keyword arguments>)
```

Calculate study power for a continuous variable (group 1 vs group 2).

# Arguments

  * `m1::Real`: study group 1 mean
  * `s1::Real`: study group 1 standard deviation
  * `n1::Int64`: study group 1 sample size
  * `m2::Real`: study group 2 mean
  * `s2::Real`: study group 2 standard deviation
  * `n2::Int64`: study group 2 sample size
  * `alpha::Float64=0.05`: the probability of type I error

# Returns

  * `p::Float64`: study power
