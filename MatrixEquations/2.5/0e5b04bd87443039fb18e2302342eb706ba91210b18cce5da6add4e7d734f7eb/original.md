```
ared(A, B, R, Q, S; scaling = 'B', pow2 = false, as = false, rtol::Real = nϵ, nrm = 1) -> (X, EVALS, F, Z, scalinfo)
```

Compute `X`, the hermitian/symmetric stabilizing solution (if `as = false`) or anti-stabilizing solution (if `as = true`) of the discrete-time algebraic Riccati equation

```
A'XA - X - (A'XB+S)(R+B'XB)^(-1)(B'XA+S') + Q = 0,
```

where `R` and `Q` are hermitian/symmetric matrices. Scalar-valued `R` and `Q` are interpreted as appropriately sized uniform scaling operators `R*I` and `Q*I`. `S`, if not specified, is set to `S = zeros(size(B))`.

To enhance the accuracy of computations, a block oriented scaling of matrices `R,` `Q` and `S` is performed  using the default setting `scaling = 'B'`. This scaling is performed only if `norm(Q) > norm(B)^2/norm(R)`. A general, eigenvalue computation oriented scaling combined with a block scaling is used if `scaling = 'G'` is selected.  An alternative, structure preserving scaling can be performed using the option `scaling = 'S'`.  A symmetric matrix equilibration based scaling is employed if `scaling = 'K'`, for which the underlying vector norm  can be specified using the keyword argument `nrm = p`, where `p = 1` is the default setting.    Experimental structure preserving scalings can be performed using the options `scaling = 'D'`, `scaling = 'R'` and `scaling = 'T'`.  Scaling can be disabled with the choice `scaling = 'N'`. If `pow2 = true`, the scaling elements are enforced to the nearest power of 2 (default: `pow2 = false`).

By default, the lower bound for the 1-norm reciprocal condition number `rtol` is `n*ϵ`, where `n` is the order of `A` and `ϵ` is the *machine epsilon* of the element type of `A`.

`EVALS` is a vector containing the (stable) eigenvalues of `A-BF`.

`F` is the stabilizing gain matrix `F = (R+B'XB)^(-1)(B'XA+S')`.

`Z = [U; V; W]` is an orthogonal basis for the relevant stable/anti-stable deflating subspace  such that `X = Sx*(V/U)*Sxi` and  `F = -Sr*(W/U)*Sxi`,  where `Sx`, `Sxi` and `Sr` are diagonal scaling matrices contained in the named tuple `scalinfo`  as `scalinfo.Sx`, `scalinfo.Sxi` and `scalinfo.Sr`, respectively.

`Reference:`

[1] W.F. Arnold, III and A.J. Laub,     Generalized Eigenproblem Algorithms and Software for Algebraic Riccati Equations,     Proc. IEEE, 72:1746-1754, 1984.

# Example

```jldoctest
julia> using LinearAlgebra

julia> A = [ 0. 1.; 0. 0. ]
2×2 Array{Float64,2}:
 0.0  1.0
 0.0  0.0

julia> B = [ 0.; sqrt(2.) ]
2-element Array{Float64,1}:
 0.0
 1.4142135623730951

julia> R = 1.
1.0

julia> Q = [ 1. -1.; -1. 1. ]
2×2 Array{Float64,2}:
  1.0  -1.0
 -1.0   1.0

julia> X, CLSEIG, F = ared(A,B,R,Q);

julia> X
2×2 Array{Float64,2}:
  1.0  -1.0
 -1.0   1.5

julia> A'*X*A-X-A'*X*B*inv(R+B'*X*B)*B'*X*A+Q
2×2 Array{Float64,2}:
  0.0          -3.33067e-16
 -3.33067e-16   8.88178e-16

julia> CLSEIG
2-element Array{Complex{Float64},1}:
 0.4999999999999998 - 0.0im
               -0.0 - 0.0im

julia> eigvals(A-B*F)
2-element Array{Float64,1}:
 -2.7755575615628914e-16
  0.5
```
