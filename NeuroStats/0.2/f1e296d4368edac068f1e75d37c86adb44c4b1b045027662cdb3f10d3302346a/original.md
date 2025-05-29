```
mde(; <keyword arguments>)
```

Calculate minimum detectable difference (MDE).

# Arguments

  * `n::Int64`: number of subject per group
  * `s::Real`: standard deviation
  * `alpha::Float64=0.05`: the probability of type I error
  * `beta::Float64=0.20`: the probability of type II error
  * `verbose::Bool=true`: print detailed output

# Returns

  * `mde::Float64`
