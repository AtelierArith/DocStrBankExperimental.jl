```
garec(A, E, B, G, R, Q, S; scaling = 'B', pw2 = false, as = false, rtol::Real = nϵ, nrm = 1) -> (X, EVALS, F, Z, scalinfo)
```

Compute `X`, the hermitian/symmetric stabilizing solution (if `as = false`) or anti-stabilizing solution (if `as = true`) of the generalized continuous-time algebraic Riccati equation

```
A'XE + E'XA - E'XGXE - (E'XB+S)R^(-1)(B'XE+S') + Q = 0,
```

where `G`, `Q` and `R` are hermitian/symmetric matrices such that `R` is nonsingular, and `E` is a nonsingular matrix. Scalar-valued `G`, `R` and `Q` are interpreted as appropriately sized uniform scaling operators `G*I`, `R*I` and `Q*I`. The generalized Schur method of [1] is used. 

To enhance the accuracy of computations, a block oriented scaling of matrices `G,` `R,` `Q` and `S` is performed  using the default setting `scaling = 'B'`. This scaling is performed only if `norm(Q) > max(norm(G), norm(B)^2/norm(R))`. A general, eigenvalue computation oriented scaling combined with a block scaling is used if `scaling = 'G'` is selected.  An alternative, structure preserving scaling can be performed using the option `scaling = 'S'`.  A symmetric matrix equilibration based scaling is employed if `scaling = 'K'`, for which the underlying vector norm  can be specified using the keyword argument `nrm = p`, where `p = 1` is the default setting.    Experimental structure preserving scalings can be performed using the options `scaling = 'D'`  or `scaling = 'T'`. Scaling can be disabled with the choice `scaling = 'N'`. If `pow2 = true`, the scaling elements are enforced to the nearest power of 2 (default: `pow2 = false`).

By default, the lower bound for the 1-norm reciprocal condition number `rtol` is `n*ϵ`, where `n` is the order of `A` and `ϵ` is the *machine epsilon* of the element type of `A`.

`EVALS` is a vector containing the (stable or anti-stable) generalized eigenvalues of the pair `(A-BF-GXE,E)`.

`F` is the stabilizing/anti-stabilizing gain matrix `F = R^(-1)(B'XE+S')`.

`Z = [U; V; W]` is an orthogonal basis for the relevant stable/anti-stable deflating subspace  such that `X = (Sx*(V/U)*Sxi)/E` and  `F = -Sr*(W/U)*Sxi`,  where `Sx`, `Sxi` and `Sr` are diagonal scaling matrices contained in the named tuple `scalinfo`  as `scalinfo.Sx`, `scalinfo.Sxi` and `scalinfo.Sr`, respectively.

`Reference:`

[1] W.F. Arnold, III and A.J. Laub,     Generalized Eigenproblem Algorithms and Software for Algebraic Riccati Equations,     Proc. IEEE, 72:1746-1754, 1984.
