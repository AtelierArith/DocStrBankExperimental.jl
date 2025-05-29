```
size_c1diff(; <keyword arguments>)
```

Calculate required sample size for detecting a difference in a continuous variable (group 1 vs population).

# Arguments

  * `s1::Real`: study study standard deviation that we want to detect
  * `s2::Real`: population standard deviation
  * `twotailed::Bool=true`: if true, the estimation is for two-tiled difference
  * `power::Float64=0.8`: the ability to detect a difference between groups (`power = 1 - beta`, where `beta` is the probability of type II error)

# Returns

  * `n::Int64`: study sample size
