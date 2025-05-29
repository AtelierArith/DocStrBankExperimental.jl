```
gared(A, E, B, R, Q, S; scaling = 'B', pow2 = false, as = false, rtol::Real = nϵ, nrm = 1) -> (X, EVALS, F, Z, scalinfo)
```

Compute `X`, the hermitian/symmetric stabilizing solution (if `as = false`) or anti-stabilizing solution (if `as = true`) of the generalized discrete-time algebraic Riccati equation

```
A'XA - E'XE - (A'XB+S)(R+B'XB)^(-1)(B'XA+S') + Q = 0,
```

where `R` and `Q` are hermitian/symmetric matrices, and `E` ist non-singular. Scalar-valued `R` and `Q` are interpreted as appropriately sized uniform scaling operators `R*I` and `Q*I`. `S`, if not specified, is set to `S = zeros(size(B))`.

To enhance the accuracy of computations, a block oriented scaling of matrices `R,` `Q` and `S` is performed  using the default setting `scaling = 'B'`. This scaling is performed only if `norm(Q) > norm(B)^2/norm(R)`. A general, eigenvalue computation oriented scaling combined with a block scaling is used if `scaling = 'G'` is selected.  An alternative, structure preserving scaling can be performed using the option `scaling = 'S'`.  A symmetric matrix equilibration based scaling is employed if `scaling = 'K'`, for which the underlying vector norm  can be specified using the keyword argument `nrm = p`, where `p = 1` is the default setting.    Experimental structure preserving scalings can be performed using the options `scaling = 'D'`, `scaling = 'R'` and `scaling = 'T'`.  Scaling can be disabled with the choice `scaling = 'N'`. If `pow2 = true`, the scaling elements are enforced to the nearest power of 2 (default: `pow2 = false`).

By default, the lower bound for the 1-norm reciprocal condition number `rtol` is `n*ϵ`, where `n` is the order of `A` and `ϵ` is the *machine epsilon* of the element type of `A`.

`EVALS` is a vector containing the (stable or anti-stable) generalized eigenvalues of the pair `(A-BF,E)`.

`F` is the stabilizing/anti-stabilizing gain matrix `F = (R+B'XB)^(-1)(B'XA+S')`.

`Z = [U; V; W]` is an orthogonal basis for the relevant stable/anti-stable deflating subspace  such that `X = (Sx*(V/U)*Sxi)/E` and  `F = -Sr*(W/U)*Sxi`,  where `Sx`, `Sxi` and `Sr` are diagonal scaling matrices contained in the named tuple `scalinfo`  as `scalinfo.Sx`, `scalinfo.Sxi` and `scalinfo.Sr`, respectively.

`Reference:`

[1] W.F. Arnold, III and A.J. Laub,     Generalized Eigenproblem Algorithms and Software for Algebraic Riccati Equations,     Proc. IEEE, 72:1746-1754, 1984.

# Example

```jldoctest
julia> using LinearAlgebra

julia> A = [-6. -2. 1.; 5. 1. -1; -4. -2. -1.]
3×3 Array{Float64,2}:
 -6.0  -2.0   1.0
  5.0   1.0  -1.0
 -4.0  -2.0  -1.0

julia> E = [10. 3. 0.; 0. 5. -1.; 0. 0. 10.]
3×3 Array{Float64,2}:
 10.0  3.0   0.0
  0.0  5.0  -1.0
  0.0  0.0  10.0

julia> B = [1. 2.; 2. 0.; 0. 1.]
3×2 Array{Float64,2}:
 1.0  2.0
 2.0  0.0
 0.0  1.0

julia> R = [1. 0.; 0. 5.]
2×2 Array{Float64,2}:
 1.0  0.0
 0.0  5.0

julia> X, CLSEIG, F = gared(A,E,B,R,2I);

julia> X
3×3 Array{Float64,2}:
  0.065865   -0.0147205  -0.0100407
 -0.0147205   0.0885939   0.0101422
 -0.0100407   0.0101422   0.0234425

julia> A'*X*A-E'*X*E-A'*X*B*inv(R+B'*X*B)*B'*X*A+2I
3×3 Array{Float64,2}:
 -1.33227e-15  -2.48412e-15   1.38778e-16
 -2.498e-15    -4.44089e-16  -6.50521e-16
  1.80411e-16  -5.91541e-16  -1.33227e-15

julia> CLSEIG
3-element Array{Complex{Float64},1}:
  -0.084235615751339 - 0.0im
  -0.190533552034239 - 0.0im
 -0.5238922629921539 - 0.0im

julia> eigvals(A-B*F,E)
3-element Array{Float64,1}:
 -0.5238922629921539
 -0.19053355203423886
 -0.08423561575133902
```
