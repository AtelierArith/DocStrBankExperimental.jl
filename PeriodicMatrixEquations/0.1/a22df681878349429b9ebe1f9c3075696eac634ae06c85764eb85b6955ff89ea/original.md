```
pslyapd(A, C; adj = true, stability_check = false) -> X
```

Solve the periodic discrete-time Lyapunov equation.

For the square `n`-th order periodic matrices `A(i)`, `i = 1, ..., pa` and  `C(i)`, `i = 1, ..., pc`  of periods `pa` and `pc`, respectively,  the periodic solution `X(i)`, `i = 1, ..., p` of period `p = lcm(pa,pc)` of the  periodic Lyapunov equation is computed:  

```
A(i)'*X(i+1)*A(i) + C(i) = X(i), i = 1, ..., p     for `adj = true`; 

A(i)*X(i)*A(i)' + C(i) = X(i+1), i = 1, ..., p     for `adj = false`.
```

The periodic matrices `A` and `C` are stored in the `n×n×pa` and `n×n×pc` 3-dimensional  arrays `A` and `C`, respectively, and `X` results as a `n×n×p` 3-dimensional array.  

Alternatively, the periodic matrices `A` and `C` can be stored in the  `pa`- and `pc`-dimensional vectors of matrices `A` and `C`, respectively, and `X` results as a `p`-dimensional vector of matrices.

If `stability_check = true`, the stability of characteristic multipliers of `A` is checked and an error is issued if any characteristic multiplier has modulus equal to or larger than one. 

The periodic discrete analog of the Bartels-Stewart method based on the periodic Schur form of the periodic matrix `A` is employed [1].

*Reference:*

[1] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.                Int. J. Control, vol, 67, pp, 69-87, 1997.
