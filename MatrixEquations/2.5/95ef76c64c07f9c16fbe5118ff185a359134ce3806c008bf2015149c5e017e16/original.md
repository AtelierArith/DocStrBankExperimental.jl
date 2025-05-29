```
X = lyapd(A, C)
```

Compute `X`, the solution of the discrete Lyapunov equation

```
   AXA' - X + C = 0,
```

where `A` is a square real or complex matrix and `C` is a square matrix. `A` must not have two eigenvalues `α` and `β` such that `αβ = 1`. The solution `X` is symmetric or hermitian if `C` is a symmetric or hermitian.

The following particular cases are also adressed:

```
X = lyapd(α*I,C)  or  X = lyapd(α,C)
```

Solve the matrix equation `(αα'-1)X + C = 0`.

```
x = lyapd(α,γ)
```

Solve the equation `(αα'-1)x + γ = 0`.

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

julia> X = lyapd(A, C)
2×2 Array{Float64,2}:
  0.2375  -0.2125
 -0.2125   0.1375

julia> A*X*A' - X + C
2×2 Array{Float64,2}:
 5.55112e-16  6.66134e-16
 2.22045e-16  4.44089e-16
```
