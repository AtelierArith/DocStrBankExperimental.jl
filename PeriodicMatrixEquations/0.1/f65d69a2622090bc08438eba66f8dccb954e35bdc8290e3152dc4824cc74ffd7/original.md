```
 psplyapd(A, C; adj = true, rtol = ϵ^(3/4)) -> U
```

Compute the upper triangular factor `U` of the solution `X = U'U` of the  periodic discrete-time Lyapunov matrix equation

```
  A'σXA + C'C = X, if adj = true,
```

or of the solution `X = UU'` of the periodic discrete-time Lyapunov matrix equation

```
  AXA' + CC' =  σX, if adj = false,
```

where `σ` is the forward shift operator `σX(i) = X(i+1)`.  The periodic matrix `A` must be stable, i.e., have all characteristic multipliers  with moduli less than one. 

The periodic matrices `A` and `C` are either stored as 3-dimensional arrays or as as vectors of matrices. 

The iterative method (Algorithm 5) of [1] and its dual version are employed.  

*Reference:*

[1] A. Varga, "Periodic Lyapunov equations: some applications and new algorithms",      Int. J. Control, vol. 67, pp. 69-87, 1997.
