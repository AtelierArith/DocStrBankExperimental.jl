```
SoftSort(; ε::Float64=1.0, rev::Bool=false, is_l2_regularized::Bool=true)
```

Constructor for [`SoftSort`](@ref).

# Arguments

  * `ε::Float64=1.0`: size of the regularization
  * `rev::Bool=false`: sort in ascending order if false
  * `is_l2_regularized::Bool=true`: use l2 regularization if true, else kl regularization
