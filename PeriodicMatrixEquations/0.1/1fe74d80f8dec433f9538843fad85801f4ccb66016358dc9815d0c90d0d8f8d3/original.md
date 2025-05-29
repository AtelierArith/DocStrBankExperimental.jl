```
pdplyap(A, C; adj = true) -> U
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

The periodic matrices `A` and `C` must have the same type, the same dimensions and commensurate periods.  The resulting upper triangular periodic matrix `U` has the period  set to the least common commensurate period of `A` and `C` and the number of subperiods is adjusted accordingly. 

The iterative method (Algorithm 5) of [1] and its dual version are employed.  

*Reference:*

[1] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.                Int. J. Control, vol, 67, pp, 69-87, 1997.
