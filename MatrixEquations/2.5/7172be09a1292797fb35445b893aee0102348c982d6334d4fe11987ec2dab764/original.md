```
arec(A, B, G, R, Q, S; scaling = 'B', pow2 = false, as = false, rtol::Real = nϵ, orth = false, nrm = 1) -> (X, EVALS, F, Z, scalinfo)
```

Computes `X`, the hermitian/symmetric stabilizing solution (if `as = false`) or anti-stabilizing solution (if `as = true`) of the continuous-time algebraic Riccati equation

```
 A'X + XA - XGX - (XB+S)R^(-1)(B'X+S') + Q = 0,
```

where `G`, `R` and `Q` are hermitian/symmetric matrices or uniform scaling operators such that `R` is nonsingular. Scalar-valued `G`, `R` and `Q` are interpreted as appropriately sized uniform scaling operators `G*I`, `R*I` and `Q*I`. `S`, if not specified, is set to `S = zeros(size(B))`.  For well conditioned `R`, the Schur method of [1] is used. For ill-conditioned `R` or if `orth = true`,  the generalized Schur method of [2] is used. 

To enhance the accuracy of computations, a block oriented scaling of matrices `G`, `R`, `Q` and `S` is performed  using the default setting `scaling = 'B'`. This scaling is performed only if `norm(Q) > max(norm(G), norm(B)^2/norm(R))`. A general, eigenvalue computation oriented scaling combined with a block scaling is used if `scaling = 'G'` is selected.  An alternative, structure preserving scaling can be performed using the option `scaling = 'S'`.  A symmetric matrix equilibration based scaling is employed if `scaling = 'K'`, for which the underlying vector norm  can be specified using the keyword argument `nrm = p`, where `p = 1` is the default setting.    If `orth = true`, two experimental scaling procedures  can be activated using the options `scaling = 'D'` and `scaling = 'T'`.  Scaling can be disabled with the choice `scaling = 'N'`.

By default, the lower bound for the 1-norm reciprocal condition number `rtol` is `n*ϵ`, where `n` is the order of `A` and `ϵ` is the *machine epsilon* of the element type of `A`.

`EVALS` is a vector containing the (stable or anti-stable) eigenvalues of `A-BF-GX`.

`F` is the stabilizing or anti-stabilizing gain matrix `F = R^(-1)(B'X+S')`.

`Z = [U; V; W]` is a basis for the relevant stable/anti-stable deflating subspace  such that `X = Sx*(V/U)*Sxi` and  `F = -Sr*(W/U)*Sxi`,  where `Sx`, `Sxi` and `Sr` are diagonal scaling matrices contained in the named tuple `scalinfo`  as `scalinfo.Sx`, `scalinfo.Sxi` and `scalinfo.Sr`, respectively. An orthogonal basis `Z` can be determined, with an increased computational cost, by setting `orth = true`.

`Reference:`

[1] Laub, A.J., A Schur Method for Solving Algebraic Riccati equations.     IEEE Trans. Auto. Contr., AC-24, pp. 913-921, 1979.

[2] W.F. Arnold, III and A.J. Laub,     Generalized Eigenproblem Algorithms and Software for Algebraic Riccati Equations,     Proc. IEEE, 72:1746-1754, 1984.
