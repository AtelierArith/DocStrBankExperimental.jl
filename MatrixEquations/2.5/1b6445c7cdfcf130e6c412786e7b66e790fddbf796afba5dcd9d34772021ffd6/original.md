```
L = lyaplikeop(A; isig = 1, adj = false, htype = false)
```

For a matrix `A`, define for `adj = false` the continuous T-Lyapunov operator `L:X -> A*X+isig*transpose(X)*transpose(A)` if `htype = false` or the continuous H-Lyapunov operator `L:X -> A*X+isig*X'*A'` if `htype = true`, or  define for `adj = true` the continuous T-Lyapunov operator `L:X -> A*transpose(X)+X*transpose(A)` if `htype = false`, or the continuous H-Lyapunov operator  `L:X -> A*X'+isig*X*A'` if `htype = true`. 
