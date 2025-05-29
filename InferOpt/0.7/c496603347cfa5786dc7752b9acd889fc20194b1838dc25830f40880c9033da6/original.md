```
SoftRank(; ε::Float64=1.0, rev::Bool=false, is_l2_regularized::Bool=true)
```

Constructor for [`SoftRank`](@ref).

# Arguments

  * `ε::Float64=1.0`: size of the regularization
  * `rev::Bool=false`: rank in ascending order if false
  * `regularization="l2": used regularization, either "l2" or "kl"
