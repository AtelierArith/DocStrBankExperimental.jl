```
L = tulyaplikeop(U; adj = false)
```

Define, for an upper triangular matrix `U`, the continuous T-Lyapunov operator `L:X -> transpose(U)*X+transpose(X)*U`, if `adj = false`, or `L:X -> U*transpose(X)+X*transpose(U)` if `adj = true`.
