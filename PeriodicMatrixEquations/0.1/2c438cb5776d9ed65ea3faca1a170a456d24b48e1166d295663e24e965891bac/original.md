```
 prdric(A, B, R, Q[, S]; itmax = 0, nodeflate = false, fast, rtol) -> (X, EVALS, F)
```

Solve the periodic Riccati difference equation

```
  X(i) = Q(i) + A(i)'X(i+1)A(i) - (A(i)'X(i+1)B(i) + S(i))*
                                 -1
         (B(i)'X(i+1)B(i) + R(i))  (A(i)'X(i+1)B(i) + S(i))'
```

and compute the stabilizing periodic state feedback

```
                                  -1
  F(i) = -(B(i)'X(i+1)B(i) + R(i))  (B(i)'X(i+1)A(i) + S(i)')
```

and the corresponding stable closed-loop characteristic multipliers of `A(i)-B(i)F(i)` in `EVALS`. 

The `n×n` and `n×m` periodic matrices `A(i)` and `B(i)` are contained in the  `PeriodicArray` objects `A` and `B`, and must have the same sampling time.  `R(i)`, `Q(i)` and `S(i)` are `m×m`, `n×n` and `n×m` periodic matrices of same sampling times  as  `A` and `B`, and such that `R(i)` and `Q(i)` are symmetric. `R(i)`, `Q(i)` and `S(i)` are contained in the  `PeriodicArray` objects `R`, `Q` and `S`.  `R`, `Q` and `S` can be alternatively provided as constant real matrices.  The resulting symmetric periodic solution `X` and periodic state feedback gain `F` have the period  set to the least common commensurate period of `A`, `B`, `R` and `Q` and the number of subperiods is adjusted accordingly. 

If `fast = true`, the fast structure exploiting pencil reduction based method of [1] is used to determine a periodic generator in `X(1)`, which allows to generate iteratively the solution  over the whole period.   If `fast = false` (default), the periodic Schur decomposition based approach of [1] is employed, applied to a  symplectic pair of periodic matrices. If `nodeflate = false` (default), the underlying periodic pencil  is preprocessed to eliminate (deflate) the infinite characteristic multipliers originating  from the problem structure. If `nodeflate = true`, no preliminary deflation is performed.

An iterative refining of the accuracy of the computed solution  can be performed by using `itmax = k`, with `k > 0` (default: `k = 0`). 

To detect singularities of involved matrices, the keyword parameter `rtol = tol` can be used to   specify the lower bound for the 1-norm reciprocal condition number.  The default value of  `tol` is `n*ϵ`, where `ϵ` is the working *machine epsilon*.

*References*

[1] A. Varga. On solving periodic Riccati equations.       Numerical Linear Algebra with Applications, 15:809-835, 2008.
