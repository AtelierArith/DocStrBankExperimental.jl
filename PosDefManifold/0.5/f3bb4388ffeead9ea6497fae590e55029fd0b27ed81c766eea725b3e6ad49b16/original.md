```
(1) sqr(P::ℍ{T}) where T<:RealOrComplex
(2) sqr(X::Union{𝕄{T}, 𝕃{T}, 𝔻{S}}) where T<:RealOrComplex where S<:Real
```

(1) Given a positive semi-definite `Hermitian` matrix $P$,  compute its square $P^{2}$.

$P$ must be flagged as Hermitian. See [typecasting matrices](@ref).

A method is provided also for generic matrices of the `Matrix` type,  `LowerTriangular` matrices and real `Diagonal` matrices (2). The output  is of the same type as the input.

**See also**: [`pow`](@ref).

**Examples**

```julia
using PosDefManifold
P=randP(5);
P²=sqr(P);  # =>  P²=PP
sqrt(P²)≈ P ? println(" ⭐ ") : println(" ⛔ ")
```
