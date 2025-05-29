```
prdlyap(A, C; stability_check = false) -> X
```

Solve the reverse-time periodic discrete-time Lyapunov equation

```
A'σXA + C = X
```

where `σ` is the forward shift operator `σX(i) = X(i+1)`.                 

The periodic matrices `A` and `C` must have the same type, the same dimensions and commensurate periods,  and additionally `C` must be symmetric. The resulting symmetric periodic solution `X` has the period  set to the least common commensurate period of `A` and `C` and the number of subperiods is adjusted accordingly. 

If `stability_check = true`, the stability of characteristic multipliers of `A` is checked and an error is issued if any characteristic multiplier has modulus equal to or larger than one. 
