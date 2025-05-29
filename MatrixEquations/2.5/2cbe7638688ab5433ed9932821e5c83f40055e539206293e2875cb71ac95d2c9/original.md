```
X = lyapc(A, C)
```

Compute `X`, the solution of the continuous Lyapunov equation

```
  AX + XA' + C = 0,
```

where `A` is a square real or complex matrix and `C` is a square matrix. `A` must not have two eigenvalues `α` and `β` such that `α+β = 0`. The solution `X` is symmetric or hermitian if `C` is a symmetric or hermitian.

The following particular cases are also adressed:

```
X = lyapc(α*I,C)  or  X = lyapc(α,C)
```

Solve the matrix equation `(α+α')X + C = 0`.

```
x = lyapc(α,γ)
```

Solve the equation `(α+α')x + γ = 0`.

# Example

```jldoctest
julia> A = [3. 4.; 5. 6.]
2×2 Array{Float64,2}:
 3.0  4.0
 5.0  6.0

julia> C = [1. 1.; 1. 2.]
2×2 Array{Float64,2}:
 1.0  1.0
 1.0  2.0

julia> X = lyapc(A, C)
2×2 Array{Float64,2}:
  0.5  -0.5
 -0.5   0.25

julia> A*X + X*A' + C
2×2 Array{Float64,2}:
 -8.88178e-16   2.22045e-16
  2.22045e-16  -4.44089e-16
```
