```
U = plyapc(A, E, B)
```

Compute `U`, the upper triangular factor of the solution `X = UU'` of the generalized continuous Lyapunov equation

```
  AXE' + EXA' + BB' = 0,
```

where `A` and `E` are square real or complex matrices and `B` is a matrix with the same number of rows as `A`. The pencil `A - λE` must have only eigenvalues with negative real parts.

```
U = plyapc(A', E', B')
```

Compute `U`, the upper triangular factor of the solution `X = U'U` of the generalized continuous Lyapunov equation

```
  A'XE + E'XA + B'B = 0,
```

where `A` and `E` are square real or complex matrices and `B` is a matrix with the same number of columns as `A`. The pencil `A - λE` must have only eigenvalues with negative real parts.

# Example

```jldoctest
julia> using LinearAlgebra

julia> A = [-2. 1.;-1. -2.]
2×2 Array{Float64,2}:
 -2.0   1.0
 -1.0  -2.0

julia> E = [1. 0.; 1. 1.]
2×2 Array{Float64,2}:
 1.0  0.0
 1.0  1.0

julia> B = [1. 1. ;1. 2.]
2×2 Array{Float64,2}:
 1.0  1.0
 1.0  2.0

julia> U = plyapc(A,E,B)
2×2 UpperTriangular{Float64,Array{Float64,2}}:
 0.408248  0.730297
  ⋅        0.547723

julia> A*U*U'*E'+E*U*U'*A'+B*B'
2×2 Array{Float64,2}:
  0.0          -8.88178e-16
 -1.33227e-15  -2.66454e-15
```
