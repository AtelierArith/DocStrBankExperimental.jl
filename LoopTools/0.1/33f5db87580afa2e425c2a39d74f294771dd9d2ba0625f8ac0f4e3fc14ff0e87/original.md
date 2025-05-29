```
getlambda()
setlambda(λ::Real)
```

`getdelta()` returns the value of $\lambda^2$ for regularizing the IR divergence. It is positive for photon-mass regularization; $0$, $-1$ and $-2$ give the  finite piece, coefficients of the $ε^{-1}$ and $ε^{-2}$, respectively. Change by `setlambda(λ)`.
