```
X = gsylv(A,B,C,D,E)
```

Solve the generalized Sylvester matrix equation

```
          AXB + CXD = E
```

using a generalized Schur form based approach. `A`, `B`, `C` and `D` are square matrices. The pencils `A-λC` and `D+λB` must be regular and must not have common eigenvalues.

The following particular cases are also adressed:

```
X = gsylv(A,B,E)
```

Solve the generalized Sylvester matrix equation `AXB  = E`.

```
X = gsylv(A,B,γ*I,E)  or  X = gsylv(A,B,γ,E)
```

Solve the generalized Sylvester matrix equation `AXB +γX = E`.

```
X = gsylv(A,B,γ*I,D,E)  or  X = gsylv(A,B,γ,D,E)
```

Solve the generalized Sylvester matrix equation `AXB +γXD = E`.

```
X = gsylv(A,B,C,δ*I,E)  or  X = gsylv(A,B,C,δ,E)
```

Solve the generalized Sylvester matrix equation `AXB +CXδ = E`.

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

julia> D = [1. -2.; -2. -1.]
2×2 Array{Float64,2}:
  1.0  -2.0
 -2.0  -1.0

julia> E = [1. -1.; -2. 2.]
2×2 Array{Float64,2}:
  1.0  -1.0
 -2.0   2.0

julia> X = gsylv(A, B, C, D, E)
2×2 Array{Float64,2}:
 -0.52094   -0.0275792
 -0.168539   0.314607

julia> A*X*B + C*X*D - E
2×2 Array{Float64,2}:
 4.44089e-16  8.88178e-16
 6.66134e-16  0.0
```
