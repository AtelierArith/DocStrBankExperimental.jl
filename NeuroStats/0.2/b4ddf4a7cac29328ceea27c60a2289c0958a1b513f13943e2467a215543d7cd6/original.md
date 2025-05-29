```
crit_t(df, alpha; <keyword arguments>)
```

Calculate critical t value.

# Arguments

  * `df::Real`: degrees of freedom (usually df = n - 1)
  * `alpha::Float64=0.05`: alpha value
  * `twotailed::Bool=true`: one- or two-tailed probability

# Returns

  * `t::Float64`

# Notes

Critical region for one- tailed probability:

  * left: `(-∞ , -t]`
  * right: `[t , ∞)`

Critical region for two-tailed probability: `(-∞ , -t] ∪ [t, ∞)`
