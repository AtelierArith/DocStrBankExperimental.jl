```
X = sylvd(A,B,C)
```

Solve the discrete Sylvester matrix equation

```
            AXB + X = C
```

using an extension of the Bartels-Stewart Schur form based approach. `A` and `B` are square matrices, and `A` and `-B` must not have common reciprocal eigenvalues.

The following particular cases are also adressed:

```
X = sylvd(α*I,B,C)  or  X = sylvd(α,B,C)
```

Solve the matrix equation `X(αB+I)  = C`.

```
X = sylvd(A,β*I,C)   or  X = sylvd(A,β,C)
```

Solve the matrix equation `(βA+I)X = C`.

```
X = sylvd(α*I,β*I,C)  or  X = sylvd(α,β,C)
```

Solve the matrix equation `(αβ+1)X = C`.

```
x = sylvd(α,β,γ)
```

Solve the equation `(αβ+1)x = γ`.

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

julia> X = sylvd(A, B, C)
2×2 Array{Float64,2}:
 -2.46667  -2.73333
  2.4       1.86667

julia> A*X*B + X - C
2×2 Array{Float64,2}:
  8.88178e-16   8.88178e-16
 -3.9968e-15   -5.55112e-15
```
