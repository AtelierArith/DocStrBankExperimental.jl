```
lanczos(N::Int,nodes::AbstractVector{<:Real},weights::AbstractVector{<:Real};removezeroweights::Bool=true)
```

Lanczos procedure–-given the nodes and weights, the function generates the first `N` recurrence coefficients of the corresponding discrete orthogonal polynomials.

Set the Boolean `removezeroweights` to `true` if zero weights should be removed.

The script is adapted from the routine RKPW in W.B. Gragg and W.J. Harrod, *The numerically stable reconstruction of Jacobi matrices from spectral data*, Numer. Math. 44 (1984), 317-335.
