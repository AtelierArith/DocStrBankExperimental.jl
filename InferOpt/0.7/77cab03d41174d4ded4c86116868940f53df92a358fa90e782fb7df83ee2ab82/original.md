```
soft_rank(θ::AbstractVector; ε=1.0, rev::Bool=false)
```

Fast differentiable ranking of vector θ.

# Arguments

  * `θ`: vector to sort

# Keyword (optional) arguments

  * `ε::Float64=1.0`: size of the regularization
  * `rev::Bool=false`: sort in ascending order if false
  * `regularization=:l2`: use l2 regularization if :l2, and kl regularization if :kl

See also [`soft_rank_l2`](@ref) and [`soft_rank_kl`](@ref).
