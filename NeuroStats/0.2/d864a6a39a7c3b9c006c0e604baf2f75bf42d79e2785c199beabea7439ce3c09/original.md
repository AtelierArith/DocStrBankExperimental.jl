```
size_p1diff(; <keyword arguments>)
```

Calculate required sample size for detecting a difference in a proportion (group 1 vs population).

# Arguments

  * `p1::Float64`: study group proportion that we want to detect
  * `p2::Float64`: population proportion
  * `power::Float64=0.8`: the ability to detect a difference between groups (`power = 1 - beta`, where `beta` is the probability of type II error)

# Returns

  * `n::Int64`: study sample size (for both study groups)
