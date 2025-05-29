```
stieltjes(N::Int,nodes_::AbstractVector{<:Real},weights_::AbstractVector{<:Real};removezeroweights::Bool=true)
```

Stieltjes procedure–-Given the nodes and weights, the function generates the first`N` recurrence coefficients of the corresponding discrete orthogonal polynomials.

Set the Boolean `removezeroweights` to `true` if zero weights should be removed.
