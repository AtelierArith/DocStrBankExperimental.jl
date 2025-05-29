```
U = plyapc(A, B)
```

Compute `U`, the upper triangular factor of the solution `X = UU'` of the continuous Lyapunov equation

```
  AX + XA' + BB' = 0,
```

where `A` is a square real or complex matrix and `B` is a matrix with the same number of rows as `A`. `A` must have only eigenvalues with negative real parts.

```
U = plyapc(A', B')
```

Compute `U`, the upper triangular factor of the solution `X = U'U` of the continuous Lyapunov equation

```
  A'X + XA + B'B = 0,
```

where `A` is a square real or complex matrix and `B` is a matrix with the same number of columns as `A`. `A` must have only eigenvalues with negative real parts.

# Example

```jldoctest
julia> using LinearAlgebra

julia> A = [-2. 1.;-1. -2.]
2×2 Array{Float64,2}:
 -2.0   1.0
 -1.0  -2.0

julia> B = [1. 1. ;1. 2.]
2×2 Array{Float64,2}:
 1.0  1.0
 1.0  2.0

julia> U = plyapc(A,B)
2×2 UpperTriangular{Float64,Array{Float64,2}}:
 0.481812  0.801784
  ⋅        0.935414

julia> A*U*U'+U*U'*A'+B*B'
2×2 Array{Float64,2}:
 0.0          8.88178e-16
 8.88178e-16  3.55271e-15
```
