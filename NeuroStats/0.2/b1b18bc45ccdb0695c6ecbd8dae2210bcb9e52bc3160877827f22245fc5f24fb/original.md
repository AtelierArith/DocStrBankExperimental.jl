```
power_c1g(; <keyword arguments>)
```

Calculate study power for a continuous variable (group 1 vs population).

# Arguments

  * `m::Real`: population mean
  * `s::Real`: population standard deviation
  * `xbar::Real`: study group mean
  * `n::Int64`: group sample size
  * `alpha::Float64=0.05`: the probability of type I error

# Returns

  * `p::Float64`: study power
