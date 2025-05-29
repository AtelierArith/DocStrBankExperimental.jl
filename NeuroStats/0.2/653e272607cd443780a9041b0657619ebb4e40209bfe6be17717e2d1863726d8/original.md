```
cl2z(ci; <keyword arguments>)
```

Convert confidence level to z score.

# Arguments

  * `cl::Float64`: confidence level
  * `twotailed::Bool=true`: one- or two-tailed probability

# Returns

  * `z::Float64`

# Notes

The confidence interval is (-z, +z) if `twotailed=true`; otherwise it is (-∞, -z) on the left and (z, +∞) on the right.
