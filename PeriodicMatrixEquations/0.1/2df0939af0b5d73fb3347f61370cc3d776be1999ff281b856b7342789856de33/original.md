```
 pfdric(A, C, R, Q[, S]; itmax = 0, nodeflate = false, fast, rtol) -> (X, EVALS, F)
```

Solve the periodic Riccati difference equation

```
  X(i+1) = Q(i) + A(i)X(i)A(i)' - (A(i)X(i)C(i)' + S(i))*
                                 -1
           (C(i)X(i)C(i)' + R(i))  (A(i)X(i)C(i)' + S(i))'
```

and compute the stabilizing periodic Kalman gain

```
                                                       -1
  F(i) = -(C(i)X(i)A(i)' + S(i)')(C(i)X(i)C(i)' + R(i))
```

and the corresponding stable Kalman filter *core* characteristic multipliers of `A(i)-F(i)C(i)` in `EVALS`. 

The `n(i+1)×n(i)` and `m×n(i)` periodic matrices `A(i)` and `C(i)` are contained in the  `PeriodicMatrix` objects `A` and `C`, and must have the same sampling time.  `R(i)`, `Q(i)` and `S(i)` are `m×m`, `n(i)×n(i)` and `m×n(i)` periodic matrices of same sampling times  as  `A` and `C`, and such that `R(i)` and `Q(i)` are symmetric.  `R`, `Q` and `S` can be alternatively provided as constant real matrices.  The resulting symmetric periodic solution `X` and Kalman filter gain `F` have the period  set to the least common commensurate period of `A`, `C`, `R` and `Q` and the number of subperiods is adjusted accordingly. 

The dual method of [1] is employed (see [`prdric`](@ref) for the description of keyword parameters).

*References*

[1] A. Varga. On solving periodic Riccati equations.       Numerical Linear Algebra with Applications, 15:809-835, 2008.   
