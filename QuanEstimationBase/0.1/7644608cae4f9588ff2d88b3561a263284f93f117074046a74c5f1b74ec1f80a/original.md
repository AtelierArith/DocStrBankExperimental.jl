```
FIM(p::Vector{R}, dp::Vector{R}; eps=GLOBAL_EPS) where {R<:Real}
```

Calculation of the classical Fisher information matrix for classical scenarios. 

  * `p`: The probability distribution.
  * `dp`: Derivatives of the probability distribution on the unknown parameters to be estimated. For example, dp[0] is the derivative vector on the first parameter.
  * `eps`: Machine epsilon.
