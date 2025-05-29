```
(X,Y) = dsylvsys(A,B,C,D,E,F)
```

Solve the dual Sylvester system of matrix equations

```
   AX + DY = C
   XB + YE = F ,
```

where `(A,D)`, `(B,E)` are pairs of square matrices of the same size. The pencils `A-λD` and `-B+λE` must be regular and must not have common eigenvalues.

# Example

```jldoctest
julia> A = [3. 4.; 5. 6.]
2×2 Array{Float64,2}:
 3.0  4.0
 5.0  6.0

julia> B = [1. 1.; 1. 2.]
2×2 Array{Float64,2}:
 1.0  1.0
 1.0  2.0

julia> C = [-1. -2.; 2. -1.]
2×2 Array{Float64,2}:
 -1.0  -2.0
  2.0  -1.0

julia> D = [1. -2.; -2. -1.]
2×2 Array{Float64,2}:
  1.0  -2.0
 -2.0  -1.0

julia> E = [1. -1.; -2. 2.]
2×2 Array{Float64,2}:
  1.0  -1.0
 -2.0   2.0

julia> F = [1. -1.; -2. 2.]
2×2 Array{Float64,2}:
  1.0  -1.0
 -2.0   2.0

julia> X, Y = dsylvsys(A, B, C, D, E, F);

julia> X
2×2 Array{Float64,2}:
  2.472  -1.648
 -1.848   1.232

julia> Y
2×2 Array{Float64,2}:
 -0.496  -0.336
  0.264   0.824

julia> A*X + D*Y - C
2×2 Array{Float64,2}:
  4.44089e-16  0.0
 -3.55271e-15  1.55431e-15

julia> X*B + Y*E - F
2×2 Array{Float64,2}:
 -8.88178e-16   0.0
  8.88178e-16  -4.44089e-16
```
