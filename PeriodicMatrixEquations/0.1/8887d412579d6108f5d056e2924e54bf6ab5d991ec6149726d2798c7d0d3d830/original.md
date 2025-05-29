```
pslyapd2(A, C, E; stability_check = false) -> (X, Y)
```

Solve a pair of periodic discrete-time Lyapunov equations.

For the square `n`-th order periodic matrices `A(i)`, `i = 1, ..., pa`,  `C(i)`, `i = 1, ..., pc`, and `E(i)`, `i = 1, ..., pe` of periods `pa`, `pc` and `pe`, respectively,  the periodic solutions `X(i)`, `i = 1, ..., p` and `Y(i)`, `i = 1, ..., p`  of period `p = lcm(pa,pc,pe)` of the periodic Lyapunov equations are computed:  

```
A(i)*X(i)*A(i)' + C(i) = X(i+1), i = 1, ..., p ,  
 
A(i)'*Y(i+1)*A(i) + E(i) = Y(i), i = 1, ..., p .
```

The periodic matrices `A`, `C` and `E` are stored in the `n×n×pa`, `n×n×pc` and `n×n×pe` 3-dimensional  arrays `A`, `C` and `E`, respectively, and `X` and `Y` result as `n×n×p` 3-dimensional arrays.  

Alternatively, the periodic matrices `A`, `C` and `E` can be stored in the  `pa`-, `pc`- and `pe`-dimensional vectors of matrices `A`, `C` and `E`, respectively, and `X` and `Y` result as `p`-dimensional vectors of matrices.

If `stability_check = true`, the stability of characteristic multipliers of `A` is checked and an error is issued if any characteristic multiplier has modulus equal to or larger than one. 

The periodic discrete analog of the Bartels-Stewart method based on the periodic Schur form of the periodic matrix `A` is employed [1].

*Reference:*

[1] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.                Int. J. Control, vol, 67, pp, 69-87, 1997.
