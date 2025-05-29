```
pdlyap2(A, C, E; stability_check = false) -> (X, Y)
```

Solve the pair of periodic discrete-time Lyapunov equations

```
AXA' + C  = σX, 
A'σYA + E = Y,
```

where `σ` is the forward shift operator `σX(i) = X(i+1)` and `σY(i) = Y(i+1)`. 

The periodic matrices `A`, `C` and `E` must have the same type, the same dimensions and commensurate periods,  and additionally `C` and `E` must be symmetric. The resulting symmetric periodic solutions `X` and `Y` have the period  set to the least common commensurate period of `A`, `C` and `E` and the number of subperiods is adjusted accordingly. 

If `stability_check = true`, the stability of characteristic multipliers of `A` is checked and an error is issued if any characteristic multiplier has modulus equal to or larger than one. 

The periodic discrete analog of the Bartels-Stewart method based on the periodic Schur form of the periodic matrix `A` is employed [1].

*Reference:*

[1] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.                Int. J. Control, vol, 67, pp, 69-87, 1997.
