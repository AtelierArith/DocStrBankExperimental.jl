```
pdlyap(A, C; adj = true, stability_check = false) -> X
```

Solve the periodic discrete-time Lyapunov equation

```
A'σXA + C = X  for adj = true
```

or 

```
AXA' + C = σX  for adj = false,
```

where `σ` is the forward shift operator `σX(i) = X(i+1)`. 

The periodic matrices `A` and `C` must have the same type, the same dimensions and commensurate periods,  and additionally `C` must be symmetric. The resulting symmetric periodic solution `X` has the period  set to the least common commensurate period of `A` and `C` and the number of subperiods is adjusted accordingly. 

If `stability_check = true`, the stability of characteristic multipliers of `A` is checked and an error is issued if any characteristic multiplier has modulus equal to or larger than one. 

The periodic discrete analog of the Bartels-Stewart method based on the periodic Schur form of the periodic matrix `A` is employed [1].

*Reference:*

[1] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.                Int. J. Control, vol, 67, pp, 69-87, 1997.
