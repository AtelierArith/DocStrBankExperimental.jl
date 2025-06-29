```
bentB = bending(B [, W], gamma=nothing, tol=eps, verbose=false)
bentB = bending(B, gamma=nothing, tol=eps, verbose=false)
```

Apply a traditional "bending" method to a symmetric matrix `B` (between-group-variance) using another symmetric matrix `W` (within-group-variance), as described by Hayes and Hill (1981). The resulting matrix is `bentB = (1-gamma)*B + gamma*v*W`, where `v` is the average eigenvalues of `B` and `gamma` is a constant between 0 and 1, which can be provided by the user or generated by this function. When `W` is omitted, the identity matrix will be used instead.

If the user supplies `gamma`, the function will simply apply the bending formula and return `bentB` without checking whether `bentB` is positive defnite or not. Otherwise (`gamma=nothing`), this function generates `gamma=1/1000`, applies bending, and returns `bentB` if it is positive definite as `minimum(eigen(bentB).values)>tol` (the default `tol` is the machine epsilon). If not, the function tries `gamma=2/1000`, `gamma=3/1000`, ..., and `gamma=1000/1000` until `bentB` becomes positive definite.

With `verbose=true`, this function prints `v` (average eigenvalue of `B`) and `gamma` that has been used for bending (default: `verbose=false`).
