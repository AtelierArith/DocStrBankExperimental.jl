```
X = sylvc(A,B,C)
```

Solve the continuous Sylvester matrix equation

```
            AX + XB = C
```

using the Bartels-Stewart Schur form based approach. `A` and `B` are square matrices, and `A` and `-B` must not have common eigenvalues.

The following particular cases are also adressed:

```
X = sylvc(α*I,B,C)  or  X = sylvc(α,B,C)
```

Solve the matrix equation `X(αI+B)  = C`.

```
X = sylvc(A,β*I,C)  or  X = sylvc(A,β,C)
```

Solve the matrix equation `(A+βI)X = C`.

```
X = sylvc(α*I,β*I,C)  or  sylvc(α,β,C)
```

Solve the matrix equation `(α+β)X = C`.

```
x = sylvc(α,β,γ)
```

Solve the equation `(α+β)x = γ`.

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

julia> X = sylvc(A, B, C)
2×2 Array{Float64,2}:
 -4.46667   1.93333
  3.73333  -1.8

julia> A*X + X*B - C
2×2 Array{Float64,2}:
  2.66454e-15  1.77636e-15
 -3.77476e-15  4.44089e-16
```
