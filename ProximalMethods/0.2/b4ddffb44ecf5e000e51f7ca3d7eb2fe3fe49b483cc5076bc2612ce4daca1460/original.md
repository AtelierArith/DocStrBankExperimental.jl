```
shrinkage!(x, λ, fac, b)
```

Compute the generalized shrinkage operator with scaling parameter `λ` at `x`, proximal operator of a quadratic function with quadratic parameters `A` and linear parameters `b` using a factorization `fac` of $I + λA$, overwriting `x`. See also `shrinkage`.
