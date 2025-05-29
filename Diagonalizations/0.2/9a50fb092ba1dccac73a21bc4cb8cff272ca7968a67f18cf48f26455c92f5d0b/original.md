```julia
function nonDiagonality(C::Union{Matrix, Diagonal, SorH})
```

Measure of deviancy from diagonality of $n⋅n$ square matrix `C`, defined as (Congedo et al., 2008)[🎓](@ref).

$\frac{\sum_{i≠j}|c_{ij}|^2}{(n-1)\sum_{i}|c_{ii}|^2}$

It is equal to $0$ if $C$ is diagonal, equal to $1$ if $C$ is perfectly uniform.

**Examples:**

```julia
using Diagonalizations
C=ones(10, 10)                   # uniform matrix
nd=nonDiagonality(C)             # must be 1
D=Diagonal(abs.(randn(10, 10)))  # diagonal matrix
nd=nonDiagonality(D)             # must be 0
```
