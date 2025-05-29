```
L = hulyaplikeop(U; adj = false)
```

Define, for an upper triangular matrix `U`, the continuous H-Lyapunov operator `L:X -> U'*X+X'*U`, if `adj = false`, `L:X -> U*X'+X*U'` if `adj = true`. 
