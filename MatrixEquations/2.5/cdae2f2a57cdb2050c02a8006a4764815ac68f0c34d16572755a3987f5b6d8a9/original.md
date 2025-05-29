```
arec(A, G, Q = 0; scaling = 'B', pow2 = false, as = false, rtol::Real = nϵ, nrm = 1) -> (X, EVALS, Z, scalinfo)
```

Compute `X`, the hermitian/symmetric stabilizing solution (if `as = false`) or anti-stabilizing solution (if `as = true`) of the continuous-time algebraic Riccati equation

```
 A'X + XA - XGX + Q = 0,
```

where `G` and `Q` are hermitian/symmetric matrices or uniform scaling operators. Scalar-valued `G` and `Q` are interpreted as appropriately sized uniform scaling operators `G*I` and `Q*I`. The Schur method of [1] is used. 

To enhance the accuracy of computations, a block scaling of matrices `G` and `Q` is performed, if   the default setting `scaling = 'B'` is used. This scaling is however performed only if `norm(Q) > norm(G)`. A general, eigenvalue computation oriented scaling combined with a block scaling is used if `scaling = 'G'` is selected.  An alternative, experimental structure preserving scaling can be performed using the option `scaling = 'S'`.  A symmetric matrix equilibration based scaling is employed if `scaling = 'K'`, for which the underlying vector norm  can be specified using the keyword argument `nrm = p`, where `p = 1` is the default setting.  Scaling can be disabled with the choice `scaling = 'N'`. If `pow2 = true`, the scaling elements are enforced to the nearest power of 2 (default: `pow2 = false`).

By default, the lower bound for the 1-norm reciprocal condition number `rtol` is `n*ϵ`, where `n` is the order of `A` and `ϵ` is the *machine epsilon* of the element type of `A`.

`EVALS` is a vector containing the (stable or anti-stable) eigenvalues of `A-GX`.

`Z = [U; V]` is an orthogonal basis for the stable/anti-stable deflating subspace such that `X = Sx*(V/U)*Sxi`,  where `Sx` and `Sxi` are diagonal scaling matrices contained in the named tuple `scalinfo`  as `scalinfo.Sx` and `scalinfo.Sxi`, respectively.

*Note:* To solve the continuous-time algebraic Riccati equation

```
 A'X + XA - XBR^(-1)B'X + Q = 0,
```

with `R` a hermitian/symmetric matrix and `B` a compatible size matrix, `G = BR^(-1)B'` must be provided.  This approach is not numerically suited when `R` is ill-conditioned and/or `B` has large norm.  

`Reference:`

[1] Laub, A.J., A Schur Method for Solving Algebraic Riccati equations.     IEEE Trans. Auto. Contr., AC-24, pp. 913-921, 1979.

# Example

```jldoctest
julia> using LinearAlgebra

julia> A = [-6. -2. 1.; 5. 1. -1; -4. -2. -1.]
3×3 Array{Float64,2}:
 -6.0  -2.0   1.0
  5.0   1.0  -1.0
 -4.0  -2.0  -1.0

julia> G = [1. 0. 0.; 0. 5. 0.; 0. 0. 10.]
3×3 Array{Float64,2}:
 1.0  0.0   0.0
 0.0  5.0   0.0
 0.0  0.0  10.0

julia> X, CLSEIG = arec(A,G,2I);

julia> X
3×3 Array{Float64,2}:
  0.459589   0.333603   -0.144406
  0.333603   0.65916    -0.0999216
 -0.144406  -0.0999216   0.340483

julia> A'*X+X*A-X*G*X+2I
3×3 Array{Float64,2}:
  2.22045e-16  4.44089e-16  -1.77636e-15
  4.44089e-16  6.66134e-16   1.11022e-16
 -1.77636e-15  1.11022e-16  -1.33227e-15

julia> CLSEIG
3-element Array{Complex{Float64},1}:
 -4.411547592296008 + 2.4222082620381102im
 -4.411547592296008 - 2.4222082620381102im
 -4.337128244724371 + 0.0im

julia> eigvals(A-G*X)
3-element Array{Complex{Float64},1}:
 -4.4115475922960075 - 2.4222082620381076im
 -4.4115475922960075 + 2.4222082620381076im
  -4.337128244724374 + 0.0im
```
