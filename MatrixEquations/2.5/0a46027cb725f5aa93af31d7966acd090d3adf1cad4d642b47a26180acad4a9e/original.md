```
X = lyapd(A, E, C)
```

Compute `X`, the solution of the generalized discrete Lyapunov equation

```
     AXA' - EXE' + C = 0,
```

where `A` and `E` are square real or complex matrices and `C` is a square matrix. The pencil `A-λE` must not have two eigenvalues `α` and `β` such that `αβ = 1`. The solution `X` is symmetric or hermitian if `C` is a symmetric or hermitian.

The following particular cases are also adressed:

```
X = lyapd(A,β*I,C)  or  X = lyapd(A,β,C)
```

Solve the matrix equation `AXA' - βXβ' + C = 0`.

```
X = lyapd(α*I,E,C)  or  X = lyapd(α,E,C)
```

Solve the matrix equation `αXα' - EXE' + C = 0`.

```
X = lyapd(α*I,β*I,C)  or  X = lyapd(α,β,C)
```

Solve the matrix equation `(αα'-ββ')X + C = 0`.

```
x = lyapd(α,β,γ)
```

Solve the equation `(αα'-ββ')x + γ = 0`.

# Example

```jldoctest
julia> A = [3. 4.; 5. 6.]
2×2 Array{Float64,2}:
 3.0  4.0
 5.0  6.0

julia> E = [ 1. 2.; 0. -1.]
2×2 Array{Float64,2}:
 1.0   2.0
 0.0  -1.0

julia> C = [1. 1.; 1. 2.]
2×2 Array{Float64,2}:
 1.0  1.0
 1.0  2.0

julia> X = lyapd(A, E, C)
2×2 Array{Float64,2}:
  1.775  -1.225
 -1.225   0.775

julia> A*X*A' - E*X*E' + C
2×2 Array{Float64,2}:
 -2.22045e-16  -4.44089e-16
 -1.33227e-15   1.11022e-15
```
