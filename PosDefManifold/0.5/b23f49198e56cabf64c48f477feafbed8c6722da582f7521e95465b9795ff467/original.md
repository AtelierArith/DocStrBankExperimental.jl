```
DiagOfProd(P::ℍ{T}, Q::ℍ{T}) where T<:RealOrComplex
```

**alias**: `dop`

Return the `Diagonal` matrix holding the diagonal of the product $PQ$  of two `Hermitian` matrices `P` and `Q`. Only the diagoanl part  of the product is computed.

**See also**: [`tr`](@ref), [`fDiag`](@ref).

**Examples**

```julia
using PosDefManifold, LinearAlgebra
P, Q=randP(5), randP(5)
DiagOfProd(P, Q)≈Diagonal(P*Q) ? println("⭐ ") : println("⛔ ")
```
