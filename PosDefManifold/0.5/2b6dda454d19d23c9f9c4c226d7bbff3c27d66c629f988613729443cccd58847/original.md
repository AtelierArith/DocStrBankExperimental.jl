```
(1) colProd(X::Union{𝕄{T}, ℍ{T}}, j::Int, l::Int)
(2) colProd(X::Union{𝕄{T}, ℍ{T}}, Y::Union{𝕄{T}, ℍ{T}}, j::Int, l::Int)
for all above: where T<:RealOrComplex
```

(1) Given a real or complex `Matrix` or `Hermitian` matrix $X$,  return the dot product of the $j^{th}$ and $l^{th}$ columns, defined as,

$\sum_{i=1}^{r} \big(x_{ij}^*x_{il}\big),$

where $r$ is the number of rows of $X$ and $^*$ denotes complex  conjugate (nothing if the matrix is real).

(2) Given real or complex `Matrix` or `Hermitian` matrices $X$ and $Y$,  return the dot product of the $j^{th}$ column of $X$ and the $l^{th}$ column  of $Y$, defined as,

$\sum_{i=1}^{r} \big(x_{ij}^*y_{il}\big),$

where $r$ is the number of rows of $X$ and of $Y$ and $^*$ is as above.

!!! note "Nota Bene"
    $X$ and of $Y$ may have a different number of columns, but must have the same number of rows.


Arguments $j$ and $l$ must be positive integers in range

  * (1) `j,l in 1:size(X, 2)`,
  * (2) `j in 1:size(X, 2), l in 1:size(Y, 2)`.

**See also**: [`normalizeCol!`](@ref), [`colNorm`](@ref).

**Examples**

```julia
using PosDefManifold
X=randn(10, 20)
p=colProd(X, 1, 3)
Y=randn(10, 30)
q=colProd(X, Y, 2, 25)
```
