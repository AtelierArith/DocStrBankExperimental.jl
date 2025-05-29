```
arec(A, B, R, Q, S; scaling = 'B', pow2 = false, as = false, rtol::Real = nϵ, orth = false, nrm = 1) -> (X, EVALS, F, Z, scalinfo)
```

Compute `X`, the hermitian/symmetric stabilizing solution (if `as = false`) or anti-stabilizing solution (if `as = true`) of the continuous-time algebraic Riccati equation

```
 A'X + XA - (XB+S)R^(-1)(B'X+S') + Q = 0,
```

where `R` and `Q` are hermitian/symmetric matrices or uniform scaling operators such that `R` is nonsingular. Scalar-valued `R` and `Q` are interpreted as appropriately sized uniform scaling operators `R*I` and `Q*I`. `S`, if not specified, is set to `S = zeros(size(B))`. The Schur method of [1] is used. 

To enhance the accuracy of computations, a block scaling of matrices `R`, `Q`  and `S` is performed, if   the default setting `scaling = 'B'` is used. This scaling is however performed only if `norm(Q) > norm(B)^2/norm(R)`. A general, eigenvalue computation oriented scaling combined with a block scaling is used if `scaling = 'G'` is selected.  An alternative, structure preserving scaling can be performed using the option `scaling = 'S'`.  A symmetric matrix equilibration based scaling is employed if `scaling = 'K'`, for which the underlying vector norm  can be specified using the keyword argument `nrm = p`, where `p = 1` is the default setting.    Experimental structure preserving scalings can be performed using the options `scaling = 'D'`  or `scaling = 'T'`. Scaling can be disabled with the choice `scaling = 'N'`. If `pow2 = true`, the scaling elements are enforced to the nearest power of 2 (default: `pow2 = false`).

By default, the lower bound for the 1-norm reciprocal condition number `rtol` is `n*ϵ`, where `n` is the order of `A` and `ϵ` is the *machine epsilon* of the element type of `A`.

`EVALS` is a vector containing the (stable or anti-stable) eigenvalues of `A-BF`.

`F` is the stabilizing or anti-stabilizing gain matrix `F = R^(-1)(B'X+S')`.

`Z = [U; V; W]` is a basis for the relevant stable/anti-stable deflating subspace  such that `X = Sx*(V/U)*Sxi` and  `F = -Sr*(W/U)*Sxi`,  where `Sx`, `Sxi` and `Sr` are diagonal scaling matrices contained in the named tuple `scalinfo`  as `scalinfo.Sx`, `scalinfo.Sxi` and `scalinfo.Sr`, respectively. An orthogonal basis `Z` can be determined, with an increased computational cost, by setting `orth = true`.

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

julia> B = [1. 2.; 2. 0.; 0. 1.]
3×2 Array{Float64,2}:
 1.0  2.0
 2.0  0.0
 0.0  1.0

julia> R = [1. 0.; 0. 5.]
2×2 Array{Float64,2}:
 1.0  0.0
 0.0  5.0

julia> X, CLSEIG, F = arec(A,B,R,2I);

julia> X
3×3 Array{Float64,2}:
  0.522588   0.303007  -0.327227
  0.303007   0.650895  -0.132608
 -0.327227  -0.132608   0.629825

julia> A'*X+X*A-X*B*inv(R)*B'*X+2I
3×3 Array{Float64,2}:
 -2.66454e-15  -1.55431e-15   8.88178e-16
 -1.55431e-15   2.22045e-15  -2.9976e-15
  9.99201e-16  -2.9976e-15    4.44089e-16

julia> CLSEIG
3-element Array{Complex{Float64},1}:
   -4.37703628399912 + 2.8107164873731247im
   -4.37703628399912 - 2.8107164873731247im
 -1.8663764577096091 + 0.0im

julia> eigvals(A-B*F)
3-element Array{Complex{Float64},1}:
  -4.377036283999118 - 2.8107164873731234im
  -4.377036283999118 + 2.8107164873731234im
 -1.8663764577096063 + 0.0im
```
