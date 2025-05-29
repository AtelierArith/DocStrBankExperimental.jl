```
smooth!(y, x, λ, f, ∇f!, y_prev)
```

Compute the proximal operator of a general smooth function `f` with in-place gradient `∇f!` and scaling parameter `λ` at `x` using L-BFGS, storing the results in `y`. See also `smooth!`. Warm starting is accomodated by the use of `y_prev`, the previous solution.
