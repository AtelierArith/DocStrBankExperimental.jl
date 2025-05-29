```
garec(A, E, G, Q = 0; scaling = 'B', pow2 = false, as = false, rtol::Real = nϵ, nrm = 1) -> (X, EVALS, Z, scalinfo)
```

Compute `X`, the hermitian/symmetric stabilizing solution (if `as = false`) or anti-stabilizing solution (if `as = true`) of the generalized continuous-time algebraic Riccati equation

```
A'XE + E'XA - E'XGXE + Q = 0,
```

where `G` and `Q` are hermitian/symmetric matrices or uniform scaling operators and `E` is a nonsingular matrix. Scalar-valued `G` and `Q` are interpreted as appropriately sized uniform scaling operators `G*I` and `Q*I`. The generalized Schur method of [1] is used. 

To enhance the accuracy of computations, a block scaling of matrices `G` and `Q` is performed, if   the default setting `scaling = 'B'` is used. This scaling is however performed only if `norm(Q) > norm(G)`. A general, eigenvalue computation oriented scaling combined with a block scaling is used if `scaling = 'G'` is selected.  An alternative, structure preserving scaling can be performed using the option `scaling = 'S'`.  A symmetric matrix equilibration based scaling is employed if `scaling = 'K'`, for which the underlying vector norm  can be specified using the keyword argument `nrm = p`, where `p = 1` is the default setting.    Scaling can be disabled with the choice `scaling = 'N'`. If `pow2 = true`, the scaling elements are enforced to the nearest power of 2 (default: `pow2 = false`).

By default, the lower bound for the 1-norm reciprocal condition number `rtol` is `n*ϵ`, where `n` is the order of `A` and `ϵ` is the *machine epsilon* of the element type of `A`.

`EVALS` is a vector containing the (stable or anti-stable) generalized eigenvalues of the pair `(A-GXE,E)`.

`Z = [U; V]` is an orthogonal basis for the stable/anti-stable deflating subspace such that `X = (Sx*(V/U)*Sxi)/E`,  where `Sx` and `Sxi` are diagonal scaling matrices contained in the named tuple `scalinfo`  as `scalinfo.Sx` and `scalinfo.Sxi`, respectively.

*Note:* To solve the continuous-time algebraic Riccati equation

```
 A'XE + E'XA - E'XBR^(-1)B'XE + Q = 0,
```

with `R` a hermitian/symmetric matrix and `B` a compatible size matrix, `G = BR^(-1)B'` must be provided.  This approach is not numerically suited when `R` is ill-conditioned and/or `B` has large norm.  

`Reference:`

[1] W.F. Arnold, III and A.J. Laub,     Generalized Eigenproblem Algorithms and Software for Algebraic Riccati Equations,     Proc. IEEE, 72:1746-1754, 1984.
