```
VaR(x̃, α)
```

Compute the value at risk at risk level `α` for the random variable `x̃`.

Risk must satisfy $α ∈ [0,1]$ and `α=0.5` computes the median and `α=1` computes the  essential infimum (smallest value with positive probability) and `α=0` returns infinity.

Solves for $\inf \{x ∈ \mathbb{R} : \mathbb{P}[x̃ ≤ x] > 1-α \}$

In general, this function is neither convex nor concave in the random variable x̃.
