```
U = plyapd(A, B)
```

Compute `U`, the upper triangular factor of the solution `X = UU'` of the discrete Lyapunov equation

```
  AXA' - X + BB' = 0,
```

where `A` is a square real or complex matrix and `B` is a matrix with the same number of rows as `A`. `A` must have only eigenvalues with moduli less than one.

```
U = plyapd(A', B')
```

Compute `U`, the upper triangular factor of the solution `X = U'U` of the discrete Lyapunov equation

```
  A'XA - X + B'B = 0,
```

where `A` is a square real or complex matrix and `B` is a matrix with the same number of columns as `A`. `A` must have only eigenvalues with moduli less than one.

# Example

```jldoctest
julia> using LinearAlgebra

julia> A = [-0.5 .1;-0.1 -0.5]
2×2 Array{Float64,2}:
 -0.5   0.1
 -0.1  -0.5

julia> B = [1. 1. ;1. 2.]
2×2 Array{Float64,2}:
 1.0  1.0
 1.0  2.0

julia> U = plyapd(A,B)
2×2 UpperTriangular{Float64,Array{Float64,2}}:
 0.670145  1.35277
  ⋅        2.67962

julia> A*U*U'*A'-U*U'+B*B'
2×2 Array{Float64,2}:
 -4.44089e-16  4.44089e-16
  4.44089e-16  1.77636e-15
```
