```
crit_z(alpha; <keyword arguments>)
```

Calculate critical z score.

# Arguments

  * `alpha::Float64=0.05`: alpha value
  * `twotailed::Bool=true`: one- or two-tailed probability

# Returns

  * `z::Float64`

# Notes

Critical region for one- tailed probability:

  * left: `(-∞ , -z]`
  * right: `[z , ∞)`

Critical region for two-tailed probability: `(-∞ , -z] ∪ [z, ∞)`
