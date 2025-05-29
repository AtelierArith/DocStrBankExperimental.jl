```
U = plyapd(A, E, B)
```

Compute `U`, the upper triangular factor of the solution `X = UU'` of the generalized discrete Lyapunov equation

```
  AXA' - EXE' + BB' = 0,
```

where `A` and `E` are square real or complex matrices and `B` is a matrix with the same number of rows as `A`. The pencil `A - λE` must have only eigenvalues with moduli less than one.

```
U = plyapd(A', E', B')
```

Compute `U`, the upper triangular factor of the solution `X = U'U` of the generalized discrete Lyapunov equation

```
  A'XA - E'XE + B'B = 0,
```

where `A` and `E` are square real or complex matrices and `B` is a matrix with the same number of columns as `A`. The pencil `A - λE` must have only eigenvalues with moduli less than one.

# Example

```jldoctest
julia> using LinearAlgebra

julia> A = [-0.5 .1;-0.1 -0.5]
2×2 Array{Float64,2}:
 -0.5   0.1
 -0.1  -0.5

julia> E = [1. 0.; 1. 1.]
2×2 Array{Float64,2}:
 1.0  0.0
 1.0  1.0

julia> B = [1. 1. ;1. 2.]
2×2 Array{Float64,2}:
 1.0  1.0
 1.0  2.0

julia> U = plyapd(A,E,B)
2×2 UpperTriangular{Float64,Array{Float64,2}}:
 1.56276  0.416976
  ⋅       1.34062

julia> A*U*U'*A'-E*U*U'*E'+B*B'
2×2 Array{Float64,2}:
 1.77636e-15  2.22045e-15
 2.22045e-15  2.66454e-15
```
