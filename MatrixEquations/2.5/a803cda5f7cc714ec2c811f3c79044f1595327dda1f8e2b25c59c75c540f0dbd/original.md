```
X = lyapc(A, E, C)
```

Compute `X`, the solution of the generalized continuous Lyapunov equation

```
 AXE' + EXA' + C = 0,
```

where `A` and `E` are square real or complex matrices and `C` is a square matrix. The pencil `A-λE` must not have two eigenvalues `α` and `β` such that `α+β = 0`. The solution `X` is symmetric or hermitian if `C` is a symmetric or hermitian.

The following particular cases are also adressed:

```
X = lyapc(A,β*I,C)  or  X = lyapc(A,β,C)
```

Solve the matrix equation `AXβ' + βXA' + C = 0`.

```
X = lyapc(α*I,E,C)  or  X = lyapc(α,E,C)
```

Solve the matrix equation `αXE' + EXα' + C = 0`.

```
X = lyapc(α*I,β*I,C)  or  X = lyapc(α,β,C)
```

Solve the matrix equation `(αβ'+α'β)X + C = 0`.

```
x = lyapc(α,β,γ)
```

Solve the equation `(αβ'+α'β)x + γ = 0`.

# Example

```jldoctest
julia> A = [3. 4.; 5. 6.]
2×2 Array{Float64,2}:
 3.0  4.0
 5.0  6.0

julia> E = [ 1. 2.; 0. 1.]
2×2 Array{Float64,2}:
 1.0  2.0
 0.0  1.0

julia> C = [1. 1.; 1. 2.]
2×2 Array{Float64,2}:
 1.0  1.0
 1.0  2.0

julia> X = lyapc(A, E, C)
2×2 Array{Float64,2}:
 -2.5   2.5
  2.5  -2.25

julia> A*X*E' + E*X*A' + C
2×2 Array{Float64,2}:
 -5.32907e-15  -2.66454e-15
 -4.44089e-15   0.0
```
